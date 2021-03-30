---
title: Отладка высокой загрузки ЦП в .NET Core
description: Руководство по отладке высокой загрузки ЦП в .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: ed22da3d53dfd1197de1f9b3c11ef31389cad690
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872799"
---
# <a name="debug-high-cpu-usage-in-net-core"></a>Отладка высокой загрузки ЦП в .NET Core

**Эта статья относится к: ✔️** пакету SDK для .NET Core 3.1 и более поздних версий

В этом руководстве описано, как выполнить отладку в случае чрезмерной загрузки ЦП. Используя предоставленный пример [веб-приложения ASP.NET Core](/samples/dotnet/samples/diagnostic-scenarios) в репозитории исходного кода, можно намеренно вызвать взаимоблокировку. Конечная точка перестанет отвечать на запросы, и в ней будут накапливаться потоки. Вы узнаете, как использовать различные средства для диагностики проблемы в этом сценарии на основе ряда ключевых диагностических данных.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
>
> - Выяснение причины высокой загрузки ЦП
> - Определение загрузки ЦП с помощью [dotnet-counters](dotnet-counters.md)
> - Использование [dotnet-trace](dotnet-trace.md) для создания трассировки
> - Профилирование производительности в PerfView
> - Диагностика и устранение причины чрезмерной загрузки ЦП

## <a name="prerequisites"></a>Предварительные требования

В этом учебнике используется:

- [Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.
- [Пример целевого объекта отладки ](/samples/dotnet/samples/diagnostic-scenarios) для активации сценария.
- [dotnet-trace](dotnet-trace.md) для вывода списка процессов и создания профиля.
- [dotnet-counters](dotnet-counters.md) для мониторинга загрузки ЦП.

## <a name="cpu-counters"></a>Счетчики ЦПУ

Прежде чем начать сбор диагностических данных, необходимо воспроизвести условие высокой загрузки ЦП. Запустите [пример приложения](/samples/dotnet/samples/diagnostic-scenarios) из корневого каталога примера с помощью следующей команды:

```dotnetcli
dotnet run
```

Чтобы узнать ИД процесса, выполните следующую команду:

```dotnetcli
dotnet-trace ps
```

Запишите ИД процесса, отображаемый в выходных данных команды. Наш ИД процесса — `22884`, но ваш будет другим. Чтобы проверить текущую загрузку ЦП, выполните команду [dotnet-counters](dotnet-counters.md):

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

`refresh-interval` — это время в секундах между опросами счетчиком значений ЦП. Результат выполнения должен быть аналогичен следующему:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

Сразу же после запуска веб-приложения ЦП совсем не используется и его загрузка отображается как равная `0%`. Перейдите по маршруту `api/diagscenario/highcpu`, используя `60000` в качестве параметра маршрута:

`https://localhost:5001/api/diagscenario/highcpu/60000`

Теперь выполните команду [dotnet-counters](dotnet-counters.md) повторно. Чтобы отслеживать только `cpu-usage`, укажите `System.Runtime[cpu-usage]` как часть команды.

```dotnetcli
dotnet-counters monitor --counters System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

Вы увидите увеличение загрузки ЦП, как показано ниже:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

В течение всего запроса загрузка ЦП будет колебаться на уровне 25 %. В зависимости от настройки главного компьютера следует ожидать изменения загрузки ЦП.

> [!TIP]
> Чтобы визуализировать еще более высокий уровень загрузки ЦП, можно запустить эту конечную точку на нескольких вкладках браузера одновременно.

На этом этапе можно с уверенностью сказать, что ЦП работает с большей загрузкой, чем ожидается.

## <a name="trace-generation"></a>Создание трассировки

При анализе медленного запроса требуется средство диагностики, которое позволяет получить представление о том, что делает код. Стандартным инструментом является профилировщик, и вы можете выбрать различные параметры профилировщика.

### <a name="linux"></a>[Linux](#tab/linux)

Средство `perf` можно использовать для создания профилей приложений .NET Core. Выйдите из предыдущего [примера целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios).

Задайте переменную среды `COMPlus_PerfMapEnabled`, чтобы приложение .NET Core создало файл `map` в каталоге `/tmp`. `perf` использует этот файл `map` для сопоставления адреса ЦП с функциями, созданными JIT-компилятором, по имени. Дополнительные сведения см. в разделе [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map) (Запись карты производительности).

Запустите [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios) в том же сеансе терминала.

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

Повторно запустите конечную точку API (`https://localhost:5001/api/diagscenario/highcpu/60000`) с высокой загрузкой ЦП. Пока она выполняется в рамках 1-минутного запроса, запустите команду `perf` с ИД процесса:

```bash
sudo perf record -p 2266 -g
```

Команда `perf` активирует процесс сбора данных производительности. Пусть она выполняется в течение примерно 20–30 секунд. Затем нажмите сочетание клавиш <kbd>CTRL+C</kbd>, чтобы выйти из процесса сбора. Для просмотра выходных данных трассировки можно использовать ту же команду `perf`.

```bash
sudo perf report -f
```

Вы также можете создать _flame-graph_ с помощью следующих команд:

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

Эта команда создает файл `flamegraph.svg`, который можно просмотреть в браузере для изучения проблемы с производительностью.

[![Изображение SVG-файла графа пламени](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

В Windows в качестве профилировщика можно использовать средство [dotnet-trace](dotnet-trace.md). Используя предыдущий [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios), снова запустите конечную точку с высокой загрузкой ЦП (`https://localhost:5001/api/diagscenario/highcpu/60000`). Пока она выполняется в рамках 1-минутного запроса, запустите команду `collect`, как показано ниже:

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

Пусть средство [dotnet-trace](dotnet-trace.md) выполняется в течение примерно 20–30 секунд. Затем нажмите клавишу <kbd>ВВОД</kbd>, чтобы выйти из процесса сбора. В результате в той же папке будет создан файл `nettrace`. Файлы `nettrace` являются отличным способом использования существующих средств анализа в Windows.

Откройте файл `nettrace` с помощью средства [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md), как показано ниже.

[![Изображение средства PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>См. также

- [dotnet-trace](dotnet-trace.md) для отображения списка процессов
- [dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти
- [dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа
- [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Отладка взаимоблокировки в .NET Core](debug-deadlock.md)
