---
title: Учебник по выполнению отладки утечки памяти
description: Узнайте, как выполнить отладку утечки памяти в .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 09777b6c9f80c28e1eec28983d605f2a2e261c92
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872747"
---
# <a name="debug-a-memory-leak-in-net-core"></a>Отладка утечки памяти в .NET Core

**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.1 и более поздних версий

Когда приложение ссылается на объекты, которым больше не требуется выполнять нужную задачу, может произойти утечка памяти. При ссылке на такие объекты сборщик мусора не сможет освободить используемую память, что часто приводит к снижению производительности и может привести к возникновению <xref:System.OutOfMemoryException>.

В этом учебнике демонстрируются средства для анализа утечки памяти в приложении .NET Core с помощью средств CLI для диагностики .NET. Если вы используете Windows, для отладки утечек памяти можно [использовать средства диагностики памяти Visual Studio](/visualstudio/profiling/memory-usage).

Здесь используется пример приложения, в котором намеренно происходит утечка памяти. Пример предоставляется для выполнения упражнения. Вы можете проанализировать приложение, в котором также непреднамеренно происходит утечка памяти.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
>
> - Изучение использования управляемой памяти с помощью [dotnet-counters](dotnet-counters.md).
> - Создание файла дампа.
> - Анализ использования памяти с помощью файла дампа.

## <a name="prerequisites"></a>Предварительные требования

В этом учебнике используется:

- [Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.
- [dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти.
- [dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа.
- [Пример целевого приложения отладки](/samples/dotnet/samples/diagnostic-scenarios/) для диагностики.

В учебнике предполагается, что пример приложения и инструменты установлены и готовы к использованию.

## <a name="examine-managed-memory-usage"></a>Изучение использования управляемой памяти

Перед началом сбора данных диагностики с целью поиска основной причины, которая привела к данному сценарию, необходимо убедиться в наличии утечки памяти (или ее увеличения). Для этого используйте [dotnet-counters](dotnet-counters.md).

Откройте окно консоли и перейдите к каталогу, в который вы скачали и распаковали [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/). Запустите целевой объект:

```dotnetcli
dotnet run
```

В отдельном окне консоли найдите идентификатор процесса:

```console
dotnet-counters ps
```

Результат должен выглядеть следующим образом:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Теперь проверьте использование управляемой памяти с помощью инструмента [dotnet-counters](dotnet-counters.md). `--refresh-interval` задает время между обновлениями (в секундах):

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Динамические выходные данные должны выглядеть следующим образом:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Рассмотрите подробнее эту строку:

```console
    GC Heap Size (MB)                                  4
```

Как видите, сразу после запуска объем управляемой динамической памяти составляет 4 МБ.

Теперь перейдите по URL-адресу `https://localhost:5001/api/diagscenario/memleak/20000`.

Обратите внимание, что объем использования памяти увеличился до 30 МБ.

```console
    GC Heap Size (MB)                                 30
```

Просмотрев данные об использовании памяти, вы можете точно определить, что происходит: утечка или увеличение памяти. Следующим шагом является сбор правильных данных для анализа памяти.

### <a name="generate-memory-dump"></a>Создание дампа памяти

При анализе возможных утечек памяти необходимо получить доступ к динамической памяти приложения. Затем можно анализировать содержимое памяти. Изучив связи между объектами, можно делать предположения о том, почему область памяти не освобождается. Общий источник диагностических данных — это дамп памяти в Windows или эквивалентный основной дамп в Linux. Чтобы создать дамп приложения .NET Core, воспользуйтесь инструментом [dotnet-dump](dotnet-dump.md).

Выполните приведенную ниже команду, чтобы создать основной дамп в Linux для предварительно запущенного [примера целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/):

```dotnetcli
dotnet-dump collect -p 4807
```

В результате в той же папке будет создан основной дамп.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Перезапуск неисправного процесса

После сбора дампа у вас должно быть достаточно данных для диагностики неисправного процесса. Если неисправный процесс запущен на рабочем сервере, это удачный момент для выполнения краткосрочного исправления проблем путем перезапуска процесса.

Вы уже завершили работу с [примером целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/) в рамках этого учебника и можете закрыть этот объект. Перейдите к терминалу, с которого запущен сервер, и нажмите клавиши <kbd>CTRL+C</kbd>.

### <a name="analyze-the-core-dump"></a>Анализ основного дампа

Теперь, когда у вас есть основной дамп, используйте инструмент [dotnet-dump](dotnet-dump.md), чтобы проанализировать его:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Где `core_20190430_185145` — это имя основного дампа, который нужно проанализировать.

> [!NOTE]
> Если отображается сообщение о том, что *libdl.so* не удалось найти, возможно, потребуется установить пакет *libc6-dev*. Дополнительные сведения см. в статье [Необходимые компоненты для .NET Core в Linux](../install/linux.md).

Отобразится командная строка для ввода команд SOS. Как правило, в первую очередь нужно просмотреть общее состояние управляемой динамической памяти:

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

В нашем примере видно, что большинство объектов принадлежат к типу `String` либо `Customer`.

Вы можете повторно выполнить команду `dumpheap` с помощью таблицы методов, чтобы получить список всех экземпляров `String`:

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Теперь можно использовать команду `gcroot` в экземпляре `System.String`, чтобы узнать, как и зачем объект становится корневым. Подождите, так как выполнение этой команды для объема памяти в 30 МБ занимает несколько минут:

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Как видно, `String` непосредственно содержится в объекте `Customer` и косвенно в объекте `CustomerCache`.

Вы можете продолжить разгрузку объектов и увидите, что большинство объектов `String` следуют той же модели. На этом этапе в результате исследования получено достаточно информации, чтобы найти основную причину утечки в коде.

Эта общая процедура позволяет определить источник основных утечек памяти.

## <a name="clean-up-resources"></a>Очистка ресурсов

В этом учебнике вы запустили пример веб-сервера. Работа этого сервера должна быть завершена, как описано в разделе [Перезапуск неисправного процесса](#restart-the-failed-process).

Вы также можете удалить созданный файл дампа.

## <a name="see-also"></a>См. также

- [dotnet-trace](dotnet-trace.md) для отображения списка процессов
- [dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти
- [dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа
- [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)
- [Отладка утечек памяти с помощью Visual Studio](/visualstudio/profiling/memory-usage)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Отладка высокой загрузки ЦП в .NET Core](debug-highcpu.md)
