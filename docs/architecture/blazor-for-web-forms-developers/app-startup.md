---
title: Запуск приложений
description: Узнайте, как определить логику запуска для приложения.
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509706"
---
# <a name="app-startup"></a>Запуск приложений

Приложения, написанные для ASP.NET, обычно имеют файл `global.asax.cs`, определяющий событие `Application_Start`, которое управляет тем, какие службы настроены и доступны как для преобразования для просмотра HTML, так и для обработки .NET. В этой главе рассматриваются небольшие различия между ASP.NET Core и Blazor Server.

## <a name="application_start-and-web-forms"></a>Application_Start и Web Forms

Метод Web Forms по умолчанию `Application_Start` разросся в течение нескольких лет для решения многих задач настройки.  Новый проект Web Forms с шаблоном по умолчанию в Visual Studio 2019 теперь содержит следующую логику конфигурации:

- `RouteConfig` — маршрутизация URL-адресов приложений.
- `BundleConfig` — объединение и минификация CSS и JavaScript.

Каждый из этих отдельных файлов находится в папке `App_Start` и запускается только один раз в начале приложения.  `RouteConfig` в шаблоне проекта по умолчанию добавляет `FriendlyUrlSettings` для Web Forms, чтобы разрешить URL-адресам приложений опустить расширение файла `.ASPX`.  Шаблон по умолчанию также содержит директиву, которая предоставляет постоянные коды состояния перенаправления HTTP (HTTP 301) для страниц `.ASPX` по понятному URL-адресу с именем файла, в котором пропущено расширение.

В ASP.NET Core и Blazor эти методы либо упрощены и объединяются в класс `Startup`, либо устраняются в пользу распространенных веб-технологий.

## <a name="blazor-server-startup-structure"></a>Структура класса Startup Blazor Server

Приложения Blazor Server размещаются поверх ASP.NET Core 3.0 или более поздней версии.  Веб-приложения ASP.NET Core настраиваются с помощью пары методов класса `Startup.cs` в корневой папке приложения.  Содержимое класса Startup по умолчанию указано ниже.

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

Как и остальная часть ASP.NET Core, класс Startup создается с принципами внедрения зависимостей.  `IConfiguration` предоставляется конструктору и скрывается в открытом свойстве для последующего доступа во время настройки.

Метод `ConfigureServices`, представленный в ASP.NET Core, позволяет настроить различные службы платформы ASP.NET Core для встроенного контейнера внедрения зависимостей платформы.  Различные методы `services.Add*` добавляют службы, которые включают такие функции, как проверка подлинности, Razor Pages, маршрутизация контроллера MVC, SignalR и взаимодействие с Blazor Server, среди многих других.  Этот метод не требовался в веб-формах, так как синтаксический анализ и обработка файлов ASPX, ASCX, ASHX и ASMX были определены ссылками на ASP.NET в файле конфигурации web.config.  Дополнительные сведения о внедрении зависимостей в ASP.NET Core доступны в [интерактивной документации](/aspnet/core/fundamentals/dependency-injection).

Метод `Configure` представляет концепцию конвейера HTTP для ASP.NET Core.  В этом методе мы объявляем сверху вниз [ПО промежуточного слоя](middleware.md), которое будет обрабатывать все запросы, отправленные в наше приложение. Большинство этих функций в конфигурации по умолчанию были разбиты по файлам конфигурации Web Forms и теперь находятся в одном месте для простоты ссылок.

Конфигурация настраиваемой страницы ошибок больше не помещается в файл `web.config`, теперь она настроена так, чтобы всегда отображаться, если среда приложения не помечена `Development`.  Кроме того, приложения ASP.NET Core настроены для предоставления защищенных страниц с помощью TLS по умолчанию, используя вызов метода `UseHttpsRedirection`.

Далее в `UseStaticFiles` указан непредвиденный метод конфигурации.  В ASP.NET Core поддержка запросов для статических файлов (таких как JavaScript, CSS и файлы изображений) должна быть явно включена. По умолчанию общедоступными могут быть только файлы в папке *wwwroot* приложения.

Следующая строка является первой, которая реплицирует один из параметров конфигурации из Web Forms: `UseRouting`.  Этот метод добавляет маршрутизатор ASP.NET Core к конвейеру, который можно настроить здесь или в отдельных файлах, к которым может быть выполнена маршрутизация.  Дополнительные сведения о конфигурации маршрутизации см. в [разделе "Маршрутизация"](pages-routing-layouts.md).

Последняя инструкция в этом методе определяет конечные точки, которые прослушивает ASP.NET Core.  Эти маршруты представляют собой доступные в Интернете расположения, к которым вы можете получить доступ на веб-сервере для получения некоторого содержимого, обрабатываемого .NET, и возвращаемого вам.  Первая запись, `MapBlazorHub`, настраивает концентратор SignalR для предоставления постоянного подключения в режиме реального времени к серверу, где обрабатывается состояние и преобразование для просмотра компонентов Blazor.  Вызов метода `MapFallbackToPage` указывает на веб-расположение страницы, которая запускает приложение Blazor, а также настраивает приложение для обработки запросов на глубокую компоновку со стороны клиента.  Эту функцию можно увидеть в действии, если открыть браузер и перейти непосредственно к обработанному Blazor маршруту в приложении, например `/counter` в шаблоне проекта по умолчанию. Запрос обрабатывается с помощью резервной страницы *_Host. cshtml*, которая затем запускает маршрутизатор Blazor и визуализирует страницу счетчика.

## <a name="upgrading-the-bundleconfig-process"></a>Обновление процесса BundleConfig

Технологии объединения таких ресурсов, как таблицы стилей CSS и файлы JavaScript, значительно развились благодаря другим технологиям, обеспечивающим быстрое развитие средств и методов управления этими ресурсами.  Для этого мы рекомендуем использовать средство командной строки узла, такое как Grunt/Gulp/WebPack, для упаковки статических ресурсов.

Средства командной строки Grunt, Gulp и WebPack и связанные с ними конфигурации могут быть добавлены в приложение, а ASP.NET Core будет тихо игнорировать эти файлы в процессе сборки приложения.  Можно добавить вызов для выполнения их задач, добавив `Target` внутри файла проекта, с синтаксисом, аналогичный приведенному ниже, который будет запускать сценарий gulp и целевой объект `min` внутри этого скрипта.

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

Дополнительные сведения о обеих стратегиях управления файлами CSS и JavaScript можно найти в документации по [Объединению и минификации статических ресурсов в ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

>[!div class="step-by-step"]
>[Назад](project-structure.md)
>[Вперед](components.md)
