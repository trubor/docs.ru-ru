---
title: Средство диагностики dotnet-dump — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-dump для накопления и анализа дампов Windows и Linux без использования отладчика машинного кода.
ms.date: 11/17/2020
ms.topic: reference
ms.openlocfilehash: 57149c9330d6057ea57a32bfa6582a73ed6b6dee
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740609"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Программа для сбора и анализа дампов (dotnet-dump)

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий

> [!NOTE]
> `dotnet-dump` для macOS поддерживается только в .NET 5.0 и более поздних версиях.

## <a name="install"></a>Установка

Есть два способа загрузки и установки `dotnet-dump`:

- **Средство dotnet global:**

  Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-dump) `dotnet-dump`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- **Прямое скачивание:**

  скачайте исполняемый файл средства, соответствующий вашей платформе:

  | OS  | Платформа |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-dump/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64) |

> [!NOTE]
> Для использования `dotnet-dump` в приложении x86 необходима соответствующая версия средства для архитектуры x86.

## <a name="synopsis"></a>Краткий обзор

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Описание

`dotnet-dump` — это средство сбора и анализа дампов в Windows и Linux, которое не задействует собственный отладчик системы (как, например, `lldb` в Linux). Это средство имеет важное значение на таких платформах, как Alpine Linux, где отсутствует полноценно работающее средство `lldb`. Средство `dotnet-dump` позволяет выполнять команды SOS для анализа сбоев и сборщика мусора (GC), но не поддерживает некоторые функции, как, например, отображение собственных кадров стека, потому что не является встроенным отладчиком.

## <a name="options"></a>Параметры

- **`--version`**

  Отображение версии служебной программы dotnet-dump.

- **`-h|--help`**

  Отображение справки в командной строке.

## <a name="commands"></a>Команды

| Команда                                     |
| ------------------------------------------- |
| [dotnet-dump collect](#dotnet-dump-collect) |
| [dotnet-dump analyze](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-dump collect

Записывает дамп из процесса.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Параметры

- **`-h|--help`**

  Отображение справки в командной строке.

- **`-p|--process-id <PID>`**

  Указывает идентификатор процесса, из которого нужно собрать дамп.

- **`-n|--name <name>`**

  Имя процесса, из которого нужно получить дамп.

- **`--type <Full|Heap|Mini>`**

  Указывает тип дампа, который определяет типы собираемых из процесса данных. Здесь возможны три варианта:

  - `Full` — самый крупный дамп, содержащий всю память, включая образы модулей.
  - `Heap` — большой и сравнительно подробный дамп, который содержит списки модулей, списки потоков, все стеки, сведения об исключениях, сведения об обработке и всю память, за исключением сопоставленных образов.
  - `Mini` — небольшой дамп, который содержит списки модулей, списки потоков, сведения об исключениях и все стеки.

  Если тип не указан, по умолчанию используется вариант `Full`.

- **`-o|--output <output_dump_path>`**

  Полный путь и имя файла, в который будет записан собранный дамп.

  Если значение не указано, используются следующие:

  - *.\dump_YYYYMMDD_HHMMSS.dmp* в ОС Windows;
  - *./core_YYYYMMDD_HHMMSS* в ОС Linux.

  YYYYMMDD обозначает формат "год/месяц/день", а HHMMSS — формат "час/минута/секунда".

- **`--diag`**

  Включает ведение журнала диагностики для сбора дампов.

> [!NOTE]
> В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-dump` будут совместно использовать одну и ту же переменную среды `TMPDIR`. В противном случае время ожидания команды истечет.

> [!NOTE]
> Чтобы собрать дамп с помощью `dotnet-dump`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя. В противном случае средство не сможет установить соединение с целевым процессом.

## <a name="dotnet-dump-analyze"></a>dotnet-dump analyze

Запускает интерактивную оболочку для просмотра дампа. Эта оболочка принимает различные [команды SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Аргументы

- **`<dump_path>`**

  Указывает путь к анализируемому файлу дампа.

### <a name="options"></a>Параметры

- **`-c|--command <debug_command>`**

  Указывает [команду](#analyze-sos-commands), которую нужно выполнить при запуске оболочки.

### <a name="analyze-sos-commands"></a>Анализ команд SOS

| Команда                             | Функция                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Отображение всех доступных команд.                                                               |
| `soshelp|help <command>`            | Отображение сведений об указанной команде.                                                               |
| `exit|quit`                         | Выход из интерактивного режима.                                                                       |
| `clrstack <arguments>`              | Обеспечивает трассировку стека только для управляемого кода.                                                  |
| `clrthreads <arguments>`            | Перечисление всех выполняемых управляемых потоков.                                                            |
| `dumpasync <arguments>`             | Отображение информации о машинах асинхронной обработки для кучи со сборкой мусора.                |
| `dumpassembly <arguments>`          | Отображение сведений о сборке, находящейся по указанному адресу.                                 |
| `dumpclass <arguments>`             | Отображение сведений о структуре `EEClass`, находящейся по указанному адресу.                  |
| `dumpdelegate <arguments>`          | Отображение сведений о делегате, находящемся по указанному адресу.                             |
| `dumpdomain <arguments>`            | Отображение сведений обо всех доменах приложений и всех сборках в указанных доменах.       |
| `dumpheap <arguments>`              | Отображение сведений о куче со сборкой мусора и статистики сборки мусора по объектам.       |
| `dumpil <arguments>`                | Отображает язык CIL, связанный с управляемым методом. |
| `dumplog <arguments>`               | Записывает в указанный файл содержимое журнала нагрузок, хранящегося в памяти.                         |
| `dumpmd <arguments>`                | Отображение сведений о структуре `MethodDesc`, находящейся по указанному адресу.               |
| `dumpmodule <arguments>`            | Отображение сведений о модуле, находящемся по указанному адресу.                               |
| `dumpmt <arguments>`                | Отображение сведений об объекте `MethodTable`, находящемся по указанному адресу.                        |
| `dumpobj <arguments>`               | Отображение сведений об объекте, находящемся по указанному адресу.                                      |
| `dso|dumpstackobjects <arguments>`  | Отображает все управляемые объекты, обнаруженные в пределах границ текущего стека.                    |
| `eeheap <arguments>`                | Отображение сведений о памяти процессов, занятой внутренними структурами данных среды выполнения.              |
| `finalizequeue <arguments>`         | Отображает все объекты, зарегистрированные для заключительной обработки.                                             |
| `gcroot <arguments>`                | Отображение сведений о ссылках (или корневых элементах) объекта, который расположен по указанному адресу.             |
| `gcwhere <arguments>`               | Отображение расположения переданного аргумента в куче со сборкой мусора.                               |
| `ip2md <arguments>`                 | Отображение структуры `MethodDesc`, которая расположена по указанному адресу в JIT-коде.                     |
| `histclear <arguments>`             | Освобождает все ресурсы, используемые семейством команд `hist*`.                                |
| `histinit <arguments>`              | Инициализирует структуры SOS из журнала нагрузки, сохраненного в отлаживаемом объекте.                     |
| `histobj <arguments>`               | Отображение перераспределений журнала нагрузок для сборки мусора, связанных с `<arguments>`.              |
| `histobjfind <arguments>`           | Отображение всех записей журнала, ссылающихся на объект по указанному адресу.              |
| `histroot <arguments>`              | Отображает сведения о повышениях и перемещениях указанного корневого элемента.        |
| `lm|modules`                        | Отображение выполняемых собственных модулей.                                                   |
| `name2ee <arguments>`               | Отображение структур `MethodTable` и `EEClass` для `<argument>`.                     |
| `pe|printexception <arguments>`     | Отображение любого производного от класса <xref:System.Exception> объекта для `<argument>`.      |
| `setsymbolserver <arguments>`       | Включение поддержки сервера символов                                                             |
| `syncblk <arguments>`               | Отображение сведений о заполнителе SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Отображение или изменение идентификатора текущего потока для команд SOS.                                  |

> [!NOTE]
> Дополнительные сведения см. в разделе [Расширение отладки SOS для .NET](sos-debugging-extension.md).

## <a name="using-dotnet-dump"></a>Использование `dotnet-dump`

Первым шагом является сборка дампа. Этот шаг можно пропустить, если уже создан основной дамп. Основные дампы могут создавать как операционная система, так и встроенная в среду выполнения .NET Core [функция создания дампа](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md).

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Теперь запустите анализ основного дампа с помощью команды `analyze`:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Это действие открывает интерактивный сеанс, который принимает команды следующего вида:

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

Чтобы получить сведения о необработанном исключении, которое привело к сбою приложения, выполните:

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a>Особые инструкции для Docker

Если вы используете Docker, для сбора дампа требуются возможности `SYS_PTRACE` (`--cap-add=SYS_PTRACE` или `--privileged`).

В образах Docker с Linux и пакетом SDK для Microsoft .NET Core некоторые команды `dotnet-dump` могут вызвать следующее исключение:

> Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception. (Необработанное исключение: System.DllNotFoundException: Не удалось загрузить общую библиотеку libdl.so или одну из ее зависимостей.)

Чтобы обойти эту проблему, установите пакет libc6-dev.

## <a name="see-also"></a>См. также раздел

- [Сбор и анализ блога дампов памяти](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [Средство анализа кучи (dotnet-gcdump)](dotnet-gcdump.md)
