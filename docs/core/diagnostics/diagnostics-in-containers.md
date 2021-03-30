---
title: Сбор диагностики в контейнерах
description: Из этой статьи вы узнаете, как использовать средства диагностики .NET Core в контейнерах Docker.
ms.date: 09/01/2020
ms.openlocfilehash: 1d0c9eadca348dad5c4fc0a395c8b371e3821262
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872760"
---
# <a name="collect-diagnostics-in-containers"></a>Сбор диагностики в контейнерах

Средства диагностики, которые используются для диагностики проблем с .NET Core в других сценариях, работают и в контейнерах Docker. Но для использования некоторых средств в контейнере нужно выполнить определенные действия. В этой статье объясняется, как использовать средства сбора трассировок производительности и дампов в контейнерах Docker.

## <a name="using-net-core-cli-tools-in-a-container"></a>Использование средств .NET Core CLI в контейнере

**Область применения средств: ✔** ️ пакет SDK для .NET Core 3.0 и более поздних версий

Глобальные средства диагностики .NET Core CLI ([`dotnet-counters`](dotnet-counters.md), [`dotnet-dump`](dotnet-dump.md), [`dotnet-gcdump`](dotnet-gcdump.md), и [`dotnet-trace`](dotnet-trace.md)) предназначены для самых разных сред и должны работать непосредственно в контейнерах Docker. Поэтому эти средства предпочтительны при сборе диагностических сведений для сценариев работы с .NET Core 3.0 или более поздней версии (либо 3.1 или более поздней версии для `dotnet-gcdump`) в контейнерах.

Единственной сложностью при применении этих средств в контейнере является то, что они устанавливаются вместе с пакетом SDK для .NET Core, а многие контейнеры Docker работают без пакета SDK для .NET Core. Одно из простых решений этой проблемы — установить средства в исходном образе Docker. Средства не требуют выполнения пакета SDK для .NET Core, достаточно установить его. Таким образом, можно создать Dockerfile с [многоэтапной сборкой](https://docs.docker.com/develop/develop-images/multistage-build/), который позволяет установить средства на этапе сборки (с пакетом SDK для .NET Core), а затем скопировать двоичные файлы в окончательный образ. Единственный недостаток этого подхода — увеличение размера образа Docker.

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

В качестве альтернативы пакет SDK для .NET Core можно установить в контейнере, если это необходимо для установки средств CLI. Учитывайте, что при установке пакета SDK для .NET Core среда выполнения .NET Core будет переустановлена. Поэтому обязательно установите версию пакета SDK, соответствующую среде выполнения в контейнере.

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a>Использование глобальных средств .NET Core CLI в контейнере расширения

Если вы хотите использовать глобальные средства диагностики .NET Core CLI для диагностики процессов в другом контейнере, учитывайте следующие дополнительные требования:

1. Контейнеры должны [совместно использовать пространство имен процесса](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (чтобы средства в контейнере расширения могли обращаться к процессам в целевом контейнере).
2. Глобальным средствам диагностики .NET Core CLI требуется доступ к файлам, которые среда выполнения .NET Core записывает в каталог /tmp. Поэтому к каталогу /tmp нужно предоставить общий доступ для целевого контейнера и контейнера расширения, подключив том. Например, для этого контейнеры должны совместно использовать общий [том](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) или том Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir). При попытке использовать средства диагностики из контейнера расширения без предоставления общего доступа к каталогу /tmp возникает ошибка, информирующая о том, что совместимая среда выполнения .NET не запущена.

## <a name="using-perfcollect-in-a-container"></a>Использование `PerfCollect` в контейнере

**Область применения: ✔** ️ .NET Core 2.1 и более поздних версий

Скрипт [`PerfCollect`](./trace-perfcollect-lttng.md) используется для сбора трассировок производительности. Это рекомендуемое средство сбора трассировок при использовании версий, предшествующих .NET Core 3.0. При использовании `PerfCollect` в контейнере учитывайте следующие требования:

1. Для `PerfCollect` требуется [возможность `SYS_ADMIN`](https://man7.org/linux/man-pages/man7/capabilities.7.html) (чтобы запустить средство `perf`). Поэтому убедитесь, что контейнер [запущен с этой возможностью](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).
2. Для `PerfCollect` требуется, чтобы некоторые переменные среды были установлены до начала профилирования приложения. Их можно задать либо в [Dockerfile](https://docs.docker.com/engine/reference/builder/#env), либо при [запуске контейнера](https://docs.docker.com/engine/reference/run/#env-environment-variables). Так как эти переменные не должны задаваться в обычных рабочих средах, как правило, они добавляются при запуске контейнера для профилирования. Две переменные, которые требуются PerfCollect:
    1. COMPlus_PerfMapEnabled=1;
    1. COMPlus_EnableEventLog=1.

### <a name="using-perfcollect-in-a-sidecar-container"></a>Использование `PerfCollect` в контейнере расширения

Если вы хотите запустить `PerfCollect` в одном контейнере для профилирования процесса .NET Core в другом контейнере, процедура будет практически аналогичной, за исключением следующего:

1. Переменные среды, упомянутые ранее (COMPlus_PerfMapEnabled и COMPlus_EnableEventLog), нужно установить для целевого контейнера (а не для того, в котором выполняется `PerfCollect`).
2. В контейнере, где выполняется `PerfCollect`, должна быть возможность `SYS_ADMIN` (не в целевом контейнере).
3. Два контейнера должны [совместно использовать пространство имен процесса](https://docs.docker.com/engine/reference/run/#pid-settings---pid).

## <a name="using-createdump-in-a-container"></a>Использование `createdump` в контейнере

**Область применения: ✔** ️ .NET Core 2.1 и более поздних версий

Как альтернативу `dotnet-dump` можно использовать [`createdump`](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) для создания основных дампов в Linux, содержащих как нативные, так и управляемые данные. Средство `createdump` устанавливается вместе со средой выполнения .NET Core. Его можно найти рядом с libcoreclr.so (обычно в папке /usr/share/dotnet/shared/Microsoft.NETCore.App/[версия]). Это средство работает в контейнере так же, как и в неконтейнерных средах Linux. Но есть одно исключение: для работы средства требуется [возможность `SYS_PTRACE`](https://man7.org/linux/man-pages/man7/capabilities.7.html). Поэтому контейнер Docker нужно [запускать с этой возможностью](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).

### <a name="using-createdump-in-a-sidecar-container"></a>Использование `createdump` в контейнере расширения

Если вы хотите использовать `createdump` для создания дампа процесса в другом контейнере, процедура будет практически аналогичной, за исключением следующего:

1. В контейнере, где выполняется `createdump`, должна быть возможность `SYS_PTRACE` (не в целевом контейнере).
2. Два контейнера должны [совместно использовать пространство имен процесса](https://docs.docker.com/engine/reference/run/#pid-settings---pid).
