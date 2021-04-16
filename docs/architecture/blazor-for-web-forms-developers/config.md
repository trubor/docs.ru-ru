---
title: Конфигурация приложения
description: Узнайте, как настроить приложения Blazor без использования ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 360d9077bc981a2e9875bb1f86b49c0029424d6e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509797"
---
# <a name="app-configuration"></a>Конфигурация приложения

Основной способ загрузки конфигурации приложения в Web Forms — с записями в файле *web.config* &mdash; либо на сервере, либо в связанном файле конфигурации, на который ссылается *web.config*. Статический объект `ConfigurationManager` можно использовать для взаимодействия с параметрами приложения, строками подключения репозитория данных и другими поставщиками расширенной конфигурации, добавленными в приложение. Обычно для просмотра взаимодействия с конфигурацией приложения отображается следующий код:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

При использовании ASP.NET Core и Blazor на стороне сервера файл *web.config* может присутствовать, если приложение размещено на сервере Windows IIS. Однако взаимодействия `ConfigurationManager` с этой конфигурацией не требуется, и вы можете получить более структурированную конфигурацию приложения из других источников. Давайте посмотрим, как собирается конфигурация и как можно получить доступ к сведениям о конфигурации из файла *web.config*.

## <a name="configuration-sources"></a>Источники конфигураций

ASP.NET Core признает наличие множества источников конфигурации, которые вы можете использовать для приложения. Платформа пытается предложить наиболее подходящие из этих функций по умолчанию. Конфигурация считывается и объединяется из этих различных источников с помощью ASP.NET Core. Более поздние загруженные значения для одного и того же ключа конфигурации имеют приоритет над более ранними значениями.

ASP.NET Core была разработана для обеспечения работы в облаке и упрощения настройки приложений для их пользователей и разработчиков. ASP.NET Core работает с учетом среды и знает, работает ли она в среде `Production` или `Development`. Индикатор среды задается в системной переменной среды `ASPNETCORE_ENVIRONMENT`. Если значение не задано, приложение по умолчанию работает в среде `Production`.

Приложение может активировать и добавить конфигурацию из нескольких источников, в зависимости от имени среды. По умолчанию конфигурация загружается из следующих ресурсов в указанном порядке:

1. файла *appsettings.jsв*, если он есть;
1. файла *appsettings.{ENVIRONMENT_NAME}.json*, если он есть;
1. файла секретов пользователя на диске, если он есть;
1. Переменные среды
1. аргументов командной строки;

## <a name="appsettingsjson-format-and-access"></a>Формат файла appsettings.jsк и доступ к нему

Файл *appsettings.jsв* может быть иерархическим со значениями, структурированными как в следующем JSON:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

При отображении с помощью вышеуказанного JSON система конфигурации преобразует дочерние значения в плоские структуры и ссылается на полные иерархические пути. Символ двоеточия (`:`) разделяет каждое свойство в иерархии. Например, ключ конфигурации `section1:key0` обращается к значению `key0` объектного литерала `section1`.

## <a name="user-secrets"></a>Секреты пользователя.

Секреты пользователя:

* Являются значениями конфигурации, хранящимися в JSON-файле на рабочей станции разработчика, за пределами папки разработки приложения.
* Загружаются только при выполнении в среде `Development`.
* Связаны с конкретным приложением.
* Управляется с помощью команды `user-secrets` интерфейса командной строки .NET.

Настройте приложение для хранения секретов, выполнив команду `user-secrets`:

```dotnetcli
dotnet user-secrets init
```

Предыдущая команда добавляет элемент `UserSecretsId` в файл проекта. Элемент содержит идентификатор GUID, который используется для связывания секретов с приложением. Затем можно определить секрет с помощью команды `set`. Пример:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Предыдущая команда делает ключ конфигурации `Parent:ApiKey` доступным на рабочей станции разработчика со значением `12345`.

Дополнительные сведения о создании, хранении и управлении секретами пользователей см. в документе [Безопасное хранения разрабатываемых секретов приложений в ASP.NET Core](/aspnet/core/security/app-secrets).

## <a name="environment-variables"></a>Переменные среды

Следующий набор значений, загружаемых в конфигурацию приложения, — это переменные среды системы. Все параметры переменных среды системы теперь доступны через API настройки. При чтении внутри приложения иерархические значения преобразуются в плоские структуры и разделяются символами двоеточия. Однако некоторые операционные системы не разрешают имена переменных среды с двоеточием. ASP.NET Core устраняет это ограничение, преобразуя значения с двойным подчеркиванием (`__`) в двоеточия при обращении к ним. Значение `Parent:ApiKey` из раздела о секретах пользователя выше можно переопределить с помощью переменной среды `Parent__ApiKey`.

## <a name="command-line-arguments"></a>аргументов командной строки;

Кроме того, конфигурацию можно указать в виде аргументов командной строки при запуске приложения. Используйте двойное тире (`--`) или прямую косую черту (`/`), чтобы указать имя устанавливаемого значения конфигурации и значение, которое необходимо настроить. Синтаксис напоминает следующие команды:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Возвращение web.config

Если вы развернули приложение в Windows на IIS, файл *web.config* по-прежнему настраивает IIS для управления приложением. По умолчанию службы IIS добавляют ссылку на модуль ASP.NET Core (ANCM). ANCM — это собственный модуль IIS, в котором размещается приложение вместо веб-сервера Kestrel. Этот раздел *web.config* напоминает следующую XML-разметку:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

Конфигурация конкретного приложения может быть определена путем вложения элемента `environmentVariables` в элемент `aspNetCore`. Значения, определенные в этом разделе, представлены в приложении ASP.NET Core как переменные среды. Переменные среды загружаются соответствующим образом во время выполнения этого сегмента запуска приложения.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Чтение конфигурации в приложении

В ASP.NET Core предоставляет конфигурацию приложения с помощью интерфейса <xref:Microsoft.Extensions.Configuration.IConfiguration>. Этот интерфейс конфигурации должны запрашивать компоненты Blazor, страницы Blazor и любые другие управляемые ASP.NET Core классы, которым требуется доступ к конфигурации. Платформа ASP.NET Core автоматически заполнит этот интерфейс разрешенной конфигурацией, настроенной ранее. На странице Blazor или в разметке Razor компонента можно внедрить объект `IConfiguration` с директивой `@inject`, расположенной в верхней части файла *.razor*, следующим образом:

```razor
@inject IConfiguration Configuration
```

Приведенная выше инструкция делает объект `IConfiguration` доступным в качестве переменной `Configuration` для всего остального шаблона Razor.

Отдельные параметры конфигурации можно прочитать, указав иерархию параметров конфигурации, которую нужно использовать в качестве параметра индексатора:

```csharp
var mySetting = Configuration["section1:key0"];
```

Вы можете извлечь все разделы конфигурации с помощью метода <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> для извлечения коллекции ключей в определенном месте с синтаксисом, аналогичным `GetSection("section1")`, чтобы получить конфигурацию для section1 из предыдущего примера.

## <a name="strongly-typed-configuration"></a>Строго типизированная конфигурация

С помощью Web Forms можно было создать строго типизированный тип конфигурации, наследуемый от типа <xref:System.Configuration.ConfigurationSection> и связанных с ним типов. `ConfigurationSection` позволяет настроить некоторые бизнес-правила и обработку для этих значений конфигурации.

В ASP.NET Core можно указать иерархию классов, которая будет принимать значения конфигурации. Это классы:

* Наследовать от родительского класса не нужно.
* Должны быть включены свойства `public`, соответствующие свойствам и ссылкам на типы для структуры конфигурации, которую вы хотите зафиксировать.

Для предыдущего образца *appsettings.js* можно было определить следующие классы для записи значений:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Эту иерархию классов можно заполнить, добавив следующую строку в метод `Startup.ConfigureServices`:

```csharp
services.Configure<MyConfig>(Configuration);
```

В оставшейся части приложения можно добавить входной параметр в классы или директиву `@inject` в шаблоны Razor типа `IOptions<MyConfig>` для получения строго типизированных параметров конфигурации. Свойство `IOptions<MyConfig>.Value` даст значение `MyConfig`, заполненное из параметров конфигурации.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Дополнительные сведения о функции параметров можно найти в документе [Шаблон параметров в ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces).

>[!div class="step-by-step"]
>[Назад](middleware.md)
>[Вперед](security-authentication-authorization.md)
