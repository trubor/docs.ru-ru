---
title: Начало работы с ДАПР
description: Рекомендации по подготовке локальной среды разработки и созданию своих первых приложений .NET с помощью ДАПР.
author: amolenk
ms.date: 02/25/2021
ms.openlocfilehash: 1b6ecd2cc2bf077375262155f0866cfef2dab708
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623815"
---
# <a name="get-started-with-dapr"></a>Начало работы с ДАПР

В первых двух главах вы узнали основные понятия о ДАПР. Пора использовать его для *тестового диска*. Эта глава поможет вам подготовить локальную среду разработки и создать два приложения ДАПР .NET.

## <a name="install-dapr-into-your-local-environment"></a>Установка ДАПР в локальной среде

Начните с установки ДАПР на компьютере разработчика. После завершения вы сможете создавать и запускать приложения ДАПР в [собственном режиме](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/).

1. [Установите интерфейс командной строки ДАПР](https://docs.dapr.io/getting-started/install-dapr-cli/). Он позволяет запускать, запускать и управлять экземплярами ДАПР. Он также обеспечивает поддержку отладки.

1. Установите [DOCKER Desktop](https://docs.docker.com/get-docker/). Если вы используете Windows, убедитесь, что на **рабочем столе DOCKER для Windows** настроено использование контейнеров Linux.

> [!NOTE]
> По умолчанию ДАПР использует контейнеры DOCKER для обеспечения оптимального набора возможностей. Чтобы запустить ДАПР за пределами DOCKER, можно пропустить этот шаг и [выполнить *тонкую* инициализацию](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/). В примерах, приведенных в этой главе, необходимо использовать контейнеры DOCKER.

1. [Инициализация ДАПР](https://docs.dapr.io/getting-started/install-dapr/). На этом шаге выполняется настройка среды разработки путем установки последних двоичных файлов и образов контейнеров ДАПР.

1. Установите [пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1).

Теперь, когда ДАПР установлен, пришло время создать свое первое приложение ДАПР!

## <a name="build-your-first-dapr-application"></a>Создание первого приложения ДАПР

Начнем с создания простого консольного приложения .NET, которое использует стандартный блок [управления состоянием ДАПР](state-management.md) .

### <a name="create-the-application"></a>Создание приложения

1. Откройте командную оболочку или терминал по своему усмотрению. Возможности работы с терминалами можно рассматривать в [Visual Studio Code](https://code.visualstudio.com/). Перейдите в корневую папку, в которой требуется построить приложение. После этого введите следующую команду, чтобы создать новое консольное приложение .NET:

    ```dotnetcli
    dotnet new console -o DaprCounter
    ```

    Команда формирует шаблон для простого приложения .NET Core "Hello World".

1. Затем перейдите к новому каталогу, созданному предыдущей командой:

    ```console
    cd DaprCounter
    ```

1. Запустите только что созданное приложение с помощью `dotnet run` команды. При этом записываются "Hello World!" на экран консоли:

    ```dotnetcli
    dotnet run
    ```

### <a name="add-dapr-state-management"></a>Добавление управления состоянием ДАПР

Далее вы будете использовать [стандартный блок управления состоянием](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) ДАПР для реализации счетчика с отслеживанием состояния в программе.

Вы можете вызывать API ДАПР на любой платформе разработки, используя встроенную поддержку ДАПР для HTTP и gRPC. Однако разработчики .NET смогут найти пакет SDK для ДАПР .NET более естественным и интуитивно понятным. Он предоставляет строго типизированный клиент .NET для вызова API-интерфейсов ДАПР. Пакет SDK для .NET также тесно интегрируется с ASP.NET Core.

1. В окне терминала добавьте `Dapr.Client` пакет NuGet в приложение:

    ```dotnetcli
    dotnet add package Dapr.Client
    ```

    > [!NOTE]
    > При работе с предварительной версией ДАПР не забудьте добавить `--prerelease` флаг к команде.

1. Откройте `Program.cs` файл в любимом редакторе и обновите его содержимое следующим кодом:

    ```csharp
    using System;
    using System.Threading.Tasks;
    using Dapr.Client;

    namespace DaprCounter
    {
        class Program
        {
            static async Task Main(string[] args)
            {
                const string storeName = "statestore";
                const string key = "counter";

                var daprClient = new DaprClientBuilder().Build();
                var counter = await daprClient.GetStateAsync<int>(storeName, key);

                while (true)
                {
                    Console.WriteLine($"Counter = {counter++}");

                    await daprClient.SaveStateAsync(storeName, key, counter);
                    await Task.Delay(1000);
                }
            }
        }
    }
    ```

    Обновленный код реализует следующие шаги.

    - Сначала `DaprClient` создается экземпляр нового экземпляра. Этот класс позволяет взаимодействовать с ДАПР расширения.
    - В хранилище состояний `DaprClient.GetStateAsync` получает значение для `counter` ключа. Если ключ не существует, возвращается значение по умолчанию `int` (то есть `0` ).
    - Затем код выполняет итерацию, записывает `counter` значение в консоль и сохраняет увеличенное значение в хранилище состояний.

1. Команда CLI ДАПР `run` запускает приложение. Он вызывает базовую среду выполнения ДАПР и обеспечивает совместную работу приложения и ДАПР расширения. Если опустить `app-id` , ДАПР создаст уникальное имя для приложения. Последний сегмент команды, `dotnet run` , предписывает среде выполнения ДАПР запустить приложение .NET Core.

    > [!IMPORTANT]
    > Необходимо принять меры, чтобы всегда передавать явный `app-id` параметр при использовании стандартного блока управления состоянием. Блок использует значение идентификатора приложения в качестве *префикса* для ключа состояния для каждой пары "ключ-значение". Если идентификатор приложения изменится, вы больше не сможете получить доступ к сохраненному ранее состоянию.

    Теперь запустите приложение с помощью следующей команды:

    ```console
    dapr run --app-id DaprCounter dotnet run
    ```

    Попробуйте остановить и перезапустить приложение. Вы увидите, что счетчик не сбрасывается. Вместо этого он продолжится из ранее сохраненного состояния. Стандартный блок ДАПР делает приложение с отслеживанием состояния.

> [!IMPORTANT]
> Важно понимать, что пример приложения взаимодействует с предварительно настроенным компонентом состояния, но не имеет прямой зависимости от него. ДАПР абстракций отделяет зависимость от зависимости. Как вы вскоре увидите, базовый компонент хранилища состояний можно изменить с помощью простого обновления конфигурации.

Возможно, вас интересует, где именно хранится состояние?

## <a name="component-configuration-files"></a>Файлы конфигурации компонентов

При первой инициализации ДАПР для локальной среды автоматически подготавливается контейнер Redis. Затем ДАПР настроил контейнер Redis как компонент хранилища состояний по умолчанию с файлом конфигурации компонента с именем `statestore.yaml` . Вот как выглядит его содержимое:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> Файлы конфигурации компонентов по умолчанию хранятся в `$HOME/.dapr/components` папке в Linux/macOS и в папке в `%USERPROFILE%\.dapr\components` Windows.

Обратите внимание на формат предыдущего файла конфигурации компонента:

- У каждого компонента есть имя. В примере выше компонент имеет имя `statestore` . Мы использовали это имя в первом примере кода, чтобы сообщить ДАПР расширения, какой компонент использовать.
- Каждый файл конфигурации компонента содержит `spec` раздел. Он содержит `type` поле, указывающее тип компонента. В `version` поле указывается версия компонента. `metadata`Поле содержит сведения, необходимые компоненту, например сведения о соединении и другие параметры. Значения метаданных будут различаться для различных типов компонентов.

ДАПР расширения может использовать любой компонент ДАПР, настроенный в вашем приложении. Но что делать, если у вас есть архитектурное обоснование, ограничивающее доступность компонента? Как ограничить компонент Redis ДАПР сидекарс, выполняющимся только в рабочей среде?

Для этого можно определить `namespace` для рабочей среды. Вы можете присвоить ему имя `production` . В автономном режиме укажите пространство имен ДАПР расширения, задав `NAMESPACE` переменную среды. При настройке ДАПР расширения будет загружать только те компоненты, которые соответствуют пространству имен. Для развертываний Kubernetes пространство имен Kubernetes определяет загруженные компоненты. В следующем примере показан компонент Redis, помещенный в `production` пространство имен. Обратите внимание на `namespace` объявление в `metadata` элементе:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> Компонент пространства имен доступен только для приложений, выполняющихся в том же пространстве имен. Если приложению ДАПР не удается загрузить компонент, убедитесь, что пространство имен приложения соответствует пространству имен компонента. Это может быть особенно непросто в автономном режиме, в котором пространство имен приложения хранится в `NAMESPACE` переменной среды.

При необходимости можно дополнительно ограничить компонент определенным приложением. В `production` пространстве имен может потребоваться ограничить доступ к кэшу Redis только `DaprCounter` приложением. Это можно сделать, указав `scopes` в конфигурации компонента. В следующем примере показано, как ограничить доступ к `statestore` компоненту Redis для приложения `DaprCounter` в `production` пространстве имен:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a>Создание приложения ДАПР с несколькими контейнерами

В первом примере вы создали простое консольное приложение .NET, которое было запущено параллельно с ДАПР расширения. Однако современные распределенные приложения часто состоят из множества движущихся частей. Они могут одновременно запускать независимые микрослужбы. Эти современные приложения обычно являются контейнерами и нуждаются в средствах оркестрации контейнеров, таких как Docker Compose или Kubernetes.

В следующем примере вы создадите многоконтейнерное приложение. Вы также будете использовать стандартный блок [вызова службы ДАПР](service-invocation.md) для взаимодействия между службами. Решение будет состоять из веб-приложения, которое получает прогнозы погоды из веб-API. Они будут выполняться в контейнере DOCKER. Вы будете использовать Docker Compose для локального запуска контейнера и включения возможностей отладки.

Убедитесь, что вы настроили локальную среду для ДАПР и установили [средства разработки .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) (инструкции доступны в начале этой главы).

Кроме того, вам потребуется выполнить этот пример с помощью [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с установленной рабочей нагрузкой **кросс-платформенной разработки .NET Core** .

### <a name="create-the-application"></a>Создание приложения

1. В Visual Studio 2019 создайте проект **веб-приложения ASP.NET Core** .

    :::image type="content" source="./media/getting-started/multicontainer-createproject.png" alt-text="Снимок экрана создания нового проекта":::

1. Назовите проект `DaprFrontEnd` и свое решение `DaprMultiContainer` :

    :::image type="content" source="./media/getting-started/multicontainer-configureproject.png" alt-text="Снимок экрана: Настройка нового проекта":::

1. Выберите **Веб-приложение**, чтобы создать веб-приложение с Razor Pages. Не выбирайте **Включение поддержки Docker**. Поддержка Docker будет добавлена позже.

    :::image type="content" source="./media/getting-started/multicontainer-createwebapp.png" alt-text="Снимок экрана создания нового веб-приложения ASP.NET Core":::

1. Добавьте ASP.NET Core проект веб-API в то же решение и вызовите его _дапрбаккенд_. Выберите **API** в качестве типа проекта. По умолчанию ДАПР расширения полагается на границу сети, чтобы ограничить доступ к общедоступному API. Поэтому снимите флажок **настроить для HTTPS**.

    :::image type="content" source="./media/getting-started/multicontainer-createwebapi.png" alt-text="Снимок экрана создания веб-API":::

### <a name="add-dapr-service-invocation"></a>Добавить вызов службы ДАПР

Теперь вы настраиваете обмен данными между службами с помощью [стандартного блока вызова службы](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)ДАПР. Вы включите веб-приложение для получения прогнозов погоды из веб-API. Стандартный блок вызова службы обладает многими преимуществами. Она включает обнаружение служб, автоматическую повторную попытку, шифрование сообщений (с помощью mTLS) и улучшенную наблюдаемость. Используйте пакет SDK для ДАПР для .NET, чтобы вызвать API вызова службы на ДАПР расширения.

1. В Visual Studio откройте консоль диспетчера пакетов (**средства > диспетчер пакетов NuGet > консоль диспетчера пакетов**) и убедитесь, что `DaprFrontEnd` это проект по умолчанию. В консоли добавьте `Dapr.AspNetCore` пакет NuGet в проект:

    ```powershell
    Install-Package Dapr.AspNetCore
    ```

    > [!NOTE]
    > Если целевая версия `Dapr.AspNetCore` предназначена для предварительной версии, необходимо указать `-Prerelease` флаг.

1. В `DaprFrontEnd` проекте откройте файл *Startup.CS* и замените `ConfigureServices` метод следующим кодом:

    ```csharp
    // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddRazorPages();
    }
    ```

    Вызов функции `AddDapr` регистрирует класс в `DaprClient` ASP.NET Core системе внедрения зависимостей. После регистрации клиента можно внедрить экземпляр `DaprClient` в код службы для взаимодействия с ДАПР расширения, стандартными блоками и компонентами.

1. Добавьте в проект новый файл класса C#  с именем веасерфорекаст `DaprFrontEnd` :

    ```csharp
    using System;

    namespace DaprFrontEnd
    {
        public class WeatherForecast
        {
            public DateTime Date { get; set; }

            public int TemperatureC { get; set; }

            public int TemperatureF { get; set; }

            public string Summary { get; set; }
        }
    }
    ```

1. Откройте файл *index.cshtml.CS* в папке *pages* и замените его содержимое следующим кодом:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Net.Http;
    using System.Threading.Tasks;
    using Dapr.Client;
    using Microsoft.AspNetCore.Mvc.RazorPages;

    namespace DaprFrontEnd.Pages
    {
        public class IndexModel : PageModel
        {
            private readonly DaprClient _daprClient;

            public IndexModel(DaprClient daprClient)
            {
                _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
            }

            public async Task OnGet()
            {
                var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                    HttpMethod.Get,
                    "daprbackend",
                    "weatherforecast");

                ViewData["WeatherForecastData"] = forecasts;
            }
        }
    }
    ```

    Вы добавляете в веб-приложение возможности ДАПР, внедряя `DaprClient` класс в `IndexModel` конструктор. В `OnGet` методе вы вызываете службу API с помощью стандартного блока вызова службы ДАПР. `OnGet`Метод вызывается каждый раз, когда пользователь посещает домашнюю страницу. `DaprClient.InvokeMethodAsync`Метод используется для вызова `weatherforecast` метода `daprbackend` службы. Вы настроите веб-API для использования в `daprbackend` качестве идентификатора своего приложения позже при настройке его для работы с ДАПР. Наконец, ответ службы сохраняется в представлении данных.

1. Замените содержимое файла *index. cshtml* в папке *pages* на следующий код. В нем отображаются прогнозы погоды, хранящиеся в данных представления для пользователя:

    ```razor
    @page
    @model IndexModel
    @{
        ViewData["Title"] = "Home page";
    }

    <div class="text-center">
        <h1 class="display-4">Welcome</h1>
        <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
        @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
        {
            <p>The forecast for @forecast.Date is @forecast.Summary!</p>
        }
    </div>
    ```

### <a name="add-container-support"></a>Добавление поддержки контейнеров

В последней части этого примера вы добавите поддержку контейнеров и запустите решение с помощью Docker Compose.

1. Щелкните проект правой кнопкой мыши `DaprFrontEnd` и выберите пункт **Добавить**  >  **поддержку контейнера Orchestrator**. Откроется диалоговое окно **Добавление поддержки контейнера Orchestrator** :

    :::image type="content" source="./media/getting-started/multicontainer-addorchestrator.png" alt-text="Снимок экрана добавления поддержки контейнера в контейнере":::

    Выберите **Docker Compose**.

1. В следующем диалоговом окне выберите **Linux** в качестве целевой ОС:

    :::image type="content" source="./media/getting-started/multicontainer-targetos.png" alt-text="Снимок экрана: Выбор целевой ОС DOCKER":::

    Visual Studio создает файл *DOCKER-Compose. yml* и файл *dockerignore* в папке **DOCKER-композиция** в решении:

    :::image type="content" source="./media/getting-started/multicontainer-dockersolution.png" alt-text="Снимок экрана проекта DOCKER-компоновки":::

    Файл *DOCKER-Compose. yml* имеет следующее содержимое:

    ```yaml
    version: "3.4"

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
    ```

    Файл *DOCKERIGNORE* содержит типы и расширения имен файлов, которые средству Docker не нужно включать в контейнер. Эти файлы связаны с средой разработки и системой управления версиями, а не с приложением или службой, которые вы развертываете.

    В корне каталога проекта *дапрфронтенд* был создан новый *Dockerfile* . *Dockerfile* — это последовательность команд, которые используются для создания образа. Дополнительные сведения см. в разделе [Справочник по Dockerfile](https://docs.docker.com/engine/reference/builder).

    *Dockerfile* содержит YAML:

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprFrontEnd/DaprFrontEnd.csproj", "DaprFrontEnd/"]
    RUN dotnet restore "DaprFrontEnd/DaprFrontEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprFrontEnd"
    RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]
    ```

    Предыдущие *Dockerfile* последовательно выполняют следующие шаги при вызове:

    1. Извлекает `mcr.microsoft.com/dotnet/aspnet:3.1` изображение и называет его `base` .
    1. Задает для рабочего каталога значение */АПП*.
    1. Предоставляет порт `80` и `443` .
    1. Извлекает `mcr.microsoft.com/dotnet/sdk:3.1` изображение и называет его `build` .
    1. Задает для рабочего каталога значение */src*.
    1. Копирует _дапрфронтенд/дапрфронтенд. csproj_ в новый каталог с именем *дапрфронтенд/*.
    1. Вызывает [`dotnet restore`](../../core/tools/dotnet-restore.md) в проекте.
    1. Копирует все из корневого каталога в корень образа.
    1. Задает для рабочего каталога значение _/СРК/дапрфронтенд_.
    1. Вызывает [`dotnet build`](../../core/tools/dotnet-build.md) в проекте.
        - Нацеливание на конфигурацию **выпуска** и выходные данные */АПП/буилд*.
    1. Инициализирует новый этап сборки из существующего `build` базового образа и называет его `publish` .
    1. Вызывает `dotnet publish` в проекте.
        - Нацеливание на конфигурацию **выпуска** и выходные данные */АПП/публиш*.
    1. Инициализирует новый этап сборки из существующего `publish` базового образа и называет его `final` .
    1. Задает для рабочего каталога значение */АПП*.
    1. Копирует `/app/publish` каталог из `publish` образа в корневую папку `final` образа.
    1. Задает точку входа как изображение `dotnet` и передает ее в `DaprFrontEnd.dll` качестве аргумента.

1. В `DaprBackEnd` проекте веб-API щелкните правой кнопкой мыши узел проекта и выберите пункт **Добавить**  >  **поддержку контейнера Orchestrator**. Выберите **DOCKER Compose**, а затем еще раз выберите **Linux** в качестве целевой операционной системы.

    В корне каталога проекта _дапрбаккенд_ был создан новый *Dockerfile* . *Dockerfile* содержит следующие YAML:

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprBackEnd/DaprBackEnd.csproj", "DaprBackEnd/"]
    RUN dotnet restore "DaprBackEnd/DaprBackEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprBackEnd"
    RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]
    ```

    Снова откройте файл *DOCKER-Compose. yml* и изучите его содержимое. Visual Studio обновил файл **DOCKER Compose** . Теперь обе службы включены:

    ```yaml
    version: '3.4'

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
    ```

1. Чтобы использовать стандартные блоки ДАПР внутри контейнерного приложения, необходимо добавить контейнеры сидекарс ДАПР в файл создания. Внимательно обновите содержимое файла *DOCKER-Compose. yml* , чтобы оно соответствовало следующему примеру. Обратите особое внимание на форматирование и отступы и не используйте вкладки.

    ```yaml
    version: '3.4'
    
    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
        ports:
          - "51000:50001"

      daprfrontend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprfrontend"

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
        ports:
          - "52000:50001"

      daprbackend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprbackend"
    ```

    В обновленном файле мы добавили `daprfrontend-dapr` и `daprbackend-dapr` сидекарс для `daprfrontend` `daprbackend` служб и соответственно. В обновленном файле Обратите особое внимание на следующие изменения:

    - Сидекарс использует `daprio/daprd:latest` образ контейнера. Использование `latest` тега не рекомендуется для рабочих сценариев. В рабочей среде лучше использовать конкретный номер версии.
    - Каждая служба, определенная в файле создания, имеет собственное сетевое пространство имен для изоляции сети. Сидекарс использует, `network_mode: "service:..."` чтобы убедиться в том, что они работают в том же пространстве имен, что и приложение. Это позволяет расширения и приложению обмениваться данными с помощью `localhost` .
    - Порты, на которых сидекарс ДАПР прослушивают обмен данными gRPC (по умолчанию 50001), должны быть предоставлены, чтобы сидекарс мог взаимодействовать друг с другом.

1. Запустите решение (<kbd>F5</kbd> или <kbd>нажмите клавиши CTRL + F5</kbd>), чтобы убедиться, что оно работает правильно. Если все настроено правильно, вы увидите данные прогноза погоды:

    :::image type="content" source="./media/getting-started/multicontainer-result.png" alt-text="Снимок экрана: окончательное решение, показывающее данные прогноза погоды":::

    На локальном компьютере с Docker Compose и Visual Studio 2019 можно установить точки останова и выполнить отладку в приложении. В рабочих сценариях рекомендуется размещать приложение в Kubernetes. Эта книга включает сопутствующее Справочное приложение [ешопондапр](https://github.com/dotnet-architecture/eShopOnDapr), которое содержит сценарии для развертывания в Kubernetes.

    Дополнительные сведения о стандартном блоке вызова службы ДАПР, используемом в этом пошаговом руководстве, см. в [главе 6](service-invocation.md).

## <a name="summary"></a>Итоги

В этой главе вы имели возможность *протестировать ДАПР диска* . С помощью пакета SDK для ДАПР .NET вы узнали, как ДАПР интегрируется с платформой приложений .NET.

Первый пример — это простое консольное приложение .NET с отслеживанием состояния, которое использовало Стандартный блок управления состоянием ДАПР.

Второй пример включал в себя приложение с несколькими контейнерами, работающее в DOCKER. Используя Visual Studio с Docker Compose, вы столкнулись с знакомым средством *отладки F5* , доступным во всех приложениях .NET.

Кроме того, вы более подробно рассматриваете файлы конфигурации компонентов ДАПР. Они настраивают фактическую реализацию инфраструктуры, используемую стандартными блоками ДАПР. Пространства имен и области можно использовать для ограничения доступа компонента к определенным средам и приложениям.

В следующих главах вы узнаете о стандартных блоках, предлагаемых ДАПР.

### <a name="references"></a>Ссылки

- [Документация по ДАПР. Приступая к работе](https://docs.dapr.io/getting-started)
- [ешопондапр](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> [Назад](dapr-at-20000-feet.md)
> [Вперед](reference-application.md)
