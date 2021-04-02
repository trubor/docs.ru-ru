---
title: Пример миграции Ешоп в ASP.NET Core
description: Пошаговое руководство по переносу существующего приложения ASP.NET MVC в ASP.NET Core с помощью примера приложения Интернет-магазина в качестве ссылки.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 119ba64134813fa17848cf9f5fe02cb1a14f8a5d
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122980"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a>Пример миграции Ешоп в ASP.NET Core

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

В этой главе вы узнаете, как перенести платформа .NET Framework приложение в .NET Core. В этой главе рассматривается пример приложения для Интернет-магазина, написанного для ASP.NET 5,0. Приложение будет использовать множество концепций и средств, описанных ранее в этой книге. Вы найдете приложение начальной точки в [репозитории *eShopModernizing* GitHub](https://github.com/dotnet-architecture/eShopModernizing). Существует несколько различных приложений-отправной точки. Эта глава посвящена *ешоплегацимвксолутион*.

Исходная версия проекта показана на рис. 4-1. Это довольно стандартное приложение ASP.NET MVC 5.

![Рис. 4-1](media/Figure4-1.png)

**Рис. 4-1.** Структура образца проекта MVC *eShopModernizing* .

В этой главе показано, как выполнить многие действия по обновлению вручную. Кроме того, [средство "помощник по обновлению .NET](https://aka.ms/dotnet-upgrade-assistant) " можно использовать для выполнения многих начальных действий, таких как преобразование файла проекта, изменение целевой платформы и обновление пакетов NuGet.

## <a name="run-apiport-to-identify-problematic-apis"></a>Запуск *ApiPort* для обнаружения проблемных API

Первым шагом в подготовке к миграции является запуск средства *ApiPort* . Это средство определяет, сколько платформа .NET Framework интерфейсов API вызывается приложением и сколько из них имеет .NET Standard или эквиваленты .NET Core. Сосредоточьтесь в основном на логике вашего приложения, а не на зависимостях сторонних производителей и обратите внимание на `System.Web` зависимости, которые потребуется перенести. Средство ApiPort было представлено в последней главе, посвященной [пониманию и обновлению зависимостей](understand-update-dependencies.md).

После [установки и настройки средства *ApiPort*](../../standard/analyzers/portability-analyzer.md)запустите анализ в Visual Studio, как показано на рис. 4-2.

![Рис. 4-2](media/Figure4-2.png)

**Рис. 4-2.** Анализ переносимости сборок в Visual Studio.

Выберите сборку веб-проекта из папки *bin* проекта, как показано на рис. 4-3.

![Рис. 4-3](media/Figure4-3.png)

**Рис. 4-3.** Выберите веб-сборку проекта.

Если решение содержит несколько проектов, можно выбрать их все. Пример *ешоп* включает только один проект MVC.

После создания отчета откройте файл и проверьте результаты. В сводке представлено общее представление о том, какой процент платформа .NET Framework вызовов вашего приложения имеет совместимые версии. На рис. 4-4 показана сводка по проекту MVC *ешоп* .

![Рис. 4-4](media/Figure4-4.png)

**Рис. 4-4.** Сводка ApiPort.

Для этого приложения около 80 процентов вызовов платформа .NET Framework совместимы. в процессе переноса необходимо устранить 20 процентов вызовов. Просмотр сведений показывает, что все несовместимые вызовы являются частью `System.Web` , что является ожидаемым несовместимостью. Зависимости от `System.Web` вызовов будут устранены, когда контроллеры и связанные классы приложения будут перенесены на более позднем этапе. На рис. 4-5 перечислены некоторые из определенных типов, обнаруженных средством.

![Рис. 4-5](media/Figure4-5.png)

**Рис. 4-5.** *ApiPort* несовместимые сведения о типе.

Большинство несовместимых типов относятся к `Controller` и различным связанным атрибутам, которые имеют эквиваленты в ASP.NET Core.

## <a name="update-project-files-and-nuget-reference-syntax"></a>Обновление файлов проекта и синтаксиса ссылок NuGet

Затем выполните миграцию из старой структуры файлов *. csproj* в более новую, более простую структуру, появившуюся в .NET Core. При этом вы также выполняете миграцию с помощью файла *packages.config* для ссылок NuGet на использование `<PackageReference>` элементов в файле проекта. Файлы проектов в старом стиле также могут использовать `<PackageReference>` элементы, поэтому обычно имеет смысл сначала перенести все ссылки на пакеты NuGet в этот формат, прежде чем выполнять обновление до нового формата файла проекта.

Файл *ешоплегацимвк. csproj* исходного проекта имеет длину 418 строк. Пример файла проекта показан на рис. 4-6. Чтобы получить представление об общем размере и сложности, в правой части изображения содержится миниатюра всего файла.

![Рис. 4-6](media/Figure4-6.png)

**Рис. 4-6.** Структура файла *ешоплегацимвк. csproj* .

Распространенным способом создания нового файла проекта для существующего проекта ASP.NET является создание нового приложения ASP.NET Core с помощью `dotnet new` или **файла**  >  **нового**  >  **проекта** в Visual Studio. Затем файлы можно скопировать из старого проекта в новый, чтобы завершить миграцию.

Помимо файла проекта C#, зависимости NuGet хранятся в отдельном *packages.configном* файле 45, как показано на рис. 4-7.

![Рис. 4-7](media/Figure4-7.png)

**Рис. 4-7**. Файл *packages.config* .

*packages.config* можно перенести в проекты библиотеки классов с помощью Visual Studio. Однако эта функциональность не работает с проектами ASP.NET. Дополнительные [сведения о миграции *packages.config* в `<PackageReference>` Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference). При наличии большого количества проектов для миграции [это средство сообщества может помочь](https://github.com/MarkKharitonov/NuGetPCToPRMigrator). Если вы используете средство для переноса файла проекта в новый формат, это следует сделать после завершения переноса всех ссылок NuGet для использования `<PackageReverence>` .

## <a name="create-new-aspnet-core-project"></a>Создание нового ASP.NET Core проекта

Добавьте новый проект ASP.NET Core в решение существующего приложения, чтобы упростить перемещение файлов, так как большая часть работы может быть выполнена в **Обозреватель решений** Visual Studio. В Visual Studio щелкните правой кнопкой мыши решение приложения и выберите команду **Добавить новый проект**. Выберите **ASP.NET Core веб-приложение** и присвойте имя новому проекту, как показано на рис. 4-8.

![Рис. 4-8](media/Figure4-8.png)

**Рис. 4-8.** Добавление нового веб-приложения ASP.NET Core.

В следующем диалоговом окне будет предложено выбрать шаблон для использования. Выберите шаблон **Пустой**. Не забудьте также изменить раскрывающийся список **.NET Core** на **платформа .NET Framework**. Выберите **ASP.NET Core 2,2**, как показано на рис. 4-9.

![Рис. 4-9](media/Figure4-9.png)

**Рис. 4-9** Выберите пустой шаблон проекта, предназначенный для платформа .NET Framework с ASP.NET Core 2,2.

### <a name="migrating-nuget-packages"></a>Перенос пакетов NuGet

Так как встроенное средство миграции для миграции *packages.config* `<PackageReference>` не работает в проектах ASP.NET, вы можете использовать вместо этого средство сообщества или выполнить миграцию вручную. [Используемое мной средство сообщества](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) использует XSL-файл для преобразования одного формата в другой. Чтобы использовать его, сначала скопируйте файл *packages.config* во вновь созданную папку проекта ASP.NET Core. Создайте резервную копию файлов, так как этот сценарий удаляет файл *packages.config* из всех папок, в которых выполняется сценарий. Затем выполните эти команды из папки проекта (или для всего решения, если хотите):

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

Первые две команды загружают файлы, чтобы они существовали локально. В последней строке выполняется сценарий. После запуска попытайтесь выполнить сборку нового проекта. Скорее всего, будут возникнет ошибки. Чтобы устранить их, необходимо устранить некоторые ссылки (например, большинство `Microsoft.AspNet` `System` пакетов и), а также удалить некоторые `xmlns` атрибуты.

В большинстве ASP.NET приложений MVC многие клиентские зависимости, такие как начальная загрузка и jQuery, были развернуты с помощью пакетов NuGet. В ASP.NET Core пакеты NuGet используются только для функций на стороне сервера. Клиентские файлы должны управляться другими способами. Просмотрите список `<PackageReference>` добавленных и удаляемых элементов, а также запишите все, что необходимо для клиентских библиотек, в том числе:

- Бутстрэп
- jQuery
- jQuery. Validation
- Modernizr
- popper.js
- Устранение

Статические клиентские файлы, установленные NuGet для этих пакетов, будут скопированы в папку *wwwroot* нового проекта и размещены там. Стоит подумать, что эти файлы по-прежнему нужны для приложения, а также имеет ли смысл продолжать их размещение или использовать сеть доставки содержимого (CDN). Этими версиями библиотеки можно управлять во время сборки с помощью таких средств, как [Либман](/aspnet/core/client-side/libman/) или [NPM](https://www.npmjs.com/). На рис. 4-10 показан полный файл *ешоппортед. csproj* после переноса ссылок на пакеты с помощью показанного средства преобразования и удаления ненужных пакетов.

![Рис. 4-10](media/Figure4-10.png)

**Рис. 4-10.** Ссылки на пакеты в файле *ешоппортед. csproj* .

Ссылки на пакет можно дополнительно сжать, сделав `<Version>1.0.0.0</Version>` элемент `Version=1.0.0.0` атрибутом `<PackageReference>` .

### <a name="migrate-static-files"></a>Миграция статических файлов

Все статические файлы, используемые приложением, включая сценарии и платформы сторонних производителей, но также пользовательские образы и таблицы стилей, должны быть скопированы из старого проекта в новый. В приложениях ASP.NET MVC доступ к файлам обычно осуществлялся в соответствии с их расположением в папке проекта. В ASP.NET Coreных приложениях доступ к этим статическим файлам будет осуществляться в зависимости от их расположения в папке *wwwroot* . Для проекта *ешоп* в следующих папках есть статические файлы:

* *Содержимое*
* *шрифты*
* *Изображения*
* *Pics*
* *Создание и запуск скриптов PowerShell из консоли Configuration Manager*

**Пустой** шаблон проекта, используемый на предыдущем шаге, не включает эту папку по умолчанию или по промежуточного слоя, необходимое для работы. Их необходимо добавить.

Добавьте папку *wwwroot* в корень проекта.

Добавьте версию 2.2.0 `Microsoft.AspNetCore.StaticFiles` пакета NuGet.

В *Startup. CS* добавьте вызов `app.UseStaticFiles()` в `Configure` методе:

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();

    // ...
}
```

Скопируйте папку *Content* из приложения ASP.NET MVC в папку *wwwroot* нового проекта.

Запустите приложение и перейдите к папке */контент/Басе.КСС* , чтобы убедиться, что статический файл правильно обрабатывается по ожидаемому пути. Продолжайте копирование остальных папок, содержащих статические файлы, в новый проект. Также необходимо скопировать файл *фавикон. ico* из корневого каталога проекта в папку *wwwroot* . На рис. 4-11 показаны результаты копирования этих файлов и их папок.

![Рис. 4-11](media/Figure4-11.png)

**Рис. 4-11.** Статические папки скопированы в папку *wwwroot* .

### <a name="migrate-c-files"></a>Перенос файлов C#

Затем скопируйте файлы C#, используемые приложением, включая стандартные папки MVC и их содержимое, например *контроллеры*, *модели*, *ViewModel* и *службы*. Скорее всего, в этих файлах потребуется внести некоторые изменения. Лучше копировать одну папку (или вложенную папку) за раз и компилировать, чтобы узнать, какие ошибки необходимо решить по мере того, как вы уходите.

Для примера *ешоп* первой папкой, которую я выбрал для переноса, является папка *Models* , включающая сущности C# и классы Entity Framework. Классы этой папки используются большинством других компонентов, поэтому они не будут работать до тех пор, пока эти классы не будут скопированы. После копирования папки и сборки компилятор выявил ошибки, связанные с отсутствием пространства имен `System.Web.Hosting` , связанным доступом к `HostingEnvironment` и ссылкой на `ConfigurationManager.AppSettings` . Решением этих проблем будет передача необходимых данных пути. для этого разрывы строк записываются в комментарий и к `TODO:` каждому из них добавляется комментарий для его трассировки. После изменения пяти строк в **список задач** отображается пять элементов и сборка проекта.

Далее будет скопирована папка *ViewModel* с одним из классов. Это просто, и сборка выполняется немедленно.

Папка *Services* будет скопирована. Классы этой папки зависят от Entity Framework классов из папки *Models* , поэтому ее необходимо скопировать после этой папки. К счастью, это слишком сложное построение без ошибок.

Это оставляет папку *Controllers* и ее два `Controller` класса. После копирования папки в новый проект и сборки возникает семь ошибок сборки. Четыре из них связаны с `ViewBag` доступом и сообщают об ошибке:

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

Чтобы устранить эту ошибку, добавьте ссылку на пакет NuGet в C#:

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

Оставшиеся три ошибки указывают типы, определенные в сборке, на которую нет ссылок. В частности, это следующие типы:

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

Давайте рассмотрим каждую ошибку один за другой. Первая ошибка возникает при попытке сослаться на `Server` свойство объекта `Controller` , который больше не существует. Цель операции — получить путь к файлу изображения в приложении:

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

Существует два возможных решения этой проблемы. Первый заключается в том, чтобы функциональные возможности оставались в таком виде. В этом случае вместо использования `Server.MapPath` следует использовать фиксированный путь, ссылающийся на файлы изображений в папке *wwwroot* . Кроме того, поскольку единственным предназначением этого метода действия является возврат статического файла изображения, ссылки на это действие в файлах представления можно обновить, чтобы ссылаться на статические файлы напрямую, что повышает производительность во время выполнения. Так как ни одна обработка не выполняется в рамках этого действия, нет никакой причины не просто обслуживать файлы напрямую. Если не тенабле обновить все ссылки на это действие, то действие может быть перезаписано для создания перенаправления к расположению статического файла.

Следующие две ошибки возникают в одном и том же частном методе в той же строке кода:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

`this.Url`И, и `this.Request` вызывают ошибки компилятора. Исходя из того, как используется этот код, его целью является создание ссылки на `PicController` действие, которое визуализирует файлы изображений. То же самое, что было обнаружено, может быть заменено прямыми ссылками на статические файлы, расположенные в папке *wwwroot*. Сейчас стоит закомментировать этот код и добавить `TODO:` комментарий для ссылки на него другим способом.

Стоит отметить, что базовый `Controller` класс, используемый `CatalogController` классом, в котором отображается этот код, по-прежнему ссылается на `System.Web.Mvc.Controller` . После обновления для использования ASP.NET Core будут устранены ошибки, которые необходимо устранить. Сначала удалите `using System.Web.Mvc;` строку из списка `using` операторов в `CatalogController` . Затем добавьте пакет NuGet `Microsoft.AspNetCore.Mvc` . Наконец, добавьте `using Microsoft.AspNetCore.Mvc;` оператор и повторите сборку приложения.

На этот раз возникает 16 ошибок:

- `Include` не является допустимым аргументом именованного атрибута (2)
- `HttpStatusCodeResult` не найдено (3)
- `HttpNotFound` не существует (3)
- `SelectList` не найдено (8)

Еще раз давайте рассмотрим эти ошибки один за другим. Сначала `SelectList` можно исправить, добавив `using Microsoft.AspNetCore.Mvc.Rendering;` , что не позволит устранить половину ошибок.

Все ссылки на `return HttpNotFound();` должны быть заменены на `return NotFound();` .

Все ссылки на `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` должны быть заменены на `return BadRequest();` .

Это просто оставляет за собой использование `Include` `[Bind]` атрибута в нескольких методах действия, которые выглядят следующим образом:

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

Приведенный выше код ограничивают привязку модели к свойствам, перечисленным в `Include` строке. В ASP.NET Core MVC `[Bind]` атрибут по-прежнему существует, но больше не требует `Include =` аргумента. Передайте список свойств непосредственно в `[Bind]` атрибут:

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

После этих изменений проект компилируется еще раз. Обычно рекомендуется использовать отдельные типы моделей для входных данных контроллера, вместо того чтобы использовать привязку модели непосредственно к модели предметной области или типам модели данных.

## <a name="migrate-views"></a>Миграция представлений

Два крупнейших ASP.NET Core функций MVC, связанных с представлениями, [Razor Pages](/aspnet/core/razor-pages/) и [вспомогательные функции тегов](/aspnet/core/mvc/views/tag-helpers/built-in/). Для первоначальной миграции мы не будем использовать ни одну из этих функций. Однако следует помнить о возможностях, если продолжить поддержку приложения после его переноса. Следующим шагом является копирование папки *views* из исходного проекта в новую. После сборки возникает девять ошибок:

- HttpContext не существует (2)
- Скрипты не существуют (5)
- Стили не существуют (1)
- Не удалось найти Хтмлстринг (1)

Исследование этих ошибок позволяет обнаружить, что большинство из них находятся в основном *_layout. cshtml*, с несколькими, относящимися к отрисовке скриптов и тегами стилей, а также при последнем перезапуске сервера, на котором размещено приложение. В следующем листинге кода показаны проблемные области в файле *_layout. cshtml* :

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

Ссылка на Modernizr может быть удалена. Ссылки на загрузку и jQuery можно заменить ссылками CDN на соответствующую версию.

Заменить `@Styles.Render` строку на:

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

Замените последние две `Scripts.Render` строки на:

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

Наконец, после начальной загрузки `<link>` добавьте дополнительные `<link>` элементы для локальных стилей, используемых вашим приложением. Для *ешоп* результат показан здесь:

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

Чтобы определить порядок, в котором `<link>` должны отображаться элементы, просмотрите код HTML, отображаемый в исходном приложении. Кроме того, ознакомьтесь с *бундлеконфиг. CS*, который в образце *ешоп* содержит следующий код, указывающий соответствующую последовательность:

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

Повторное создание показывает еще одну ошибку при загрузке проверки jQuery в представлениях *создания* и *редактирования* . Замените его следующим сценарием:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

Последнее, что нужно исправить в представлениях, — это ссылка на, `Session` чтобы показать, как долго выполняется приложение и на какой компьютер. Эти данные можно отобразить непосредственно в *_layout. cshtml* сайта с помощью `System.Environment.MachineName` и `System.Diagnostics.Process.GetCurrentProcess().StartTime` :

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@Environment.MachineName - @System.Diagnostics.Process.GetCurrentProcess().StartTime.ToString() UTC</small>
</section>
```

На этом этапе приложение будет успешно построено. Однако при попытке запустить его просто выдается *Hello World!* Поскольку **пустой** шаблон ASP.NET Core настроен для вывода в ответ на любой запрос. В следующем разделе я завершаю миграцию, настраивая приложение для использования ASP.NET Core MVC, включая внедрение и настройку зависимостей. После этого приложение должно запуститься. Затем будет пора исправить `TODO:` созданные ранее задачи.

## <a name="migrate-app-startup-components"></a>Перенос компонентов запуска приложений

Последний шаг миграции заключается в том, чтобы выполнить задачи запуска приложения из *Global. asax* и классов, которые он вызывает, и перенести их в ASP.NET Core эквиваленты. Эти задачи включают в себя настройку модели MVC, настройку внедрения зависимостей и работу с новой системой конфигурации. В ASP.NET Core эти задачи обрабатываются в файле *Startup. CS* .

### <a name="configure-mvc"></a>Настройка MVC

Исходное приложение ASP.NET MVC содержит следующий код в `Application_Start` *Global. asax*, который запускается при запуске приложения:

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

Просматривая эти строки по одному, `RegisterContainer` метод настраивает внедрение зависимостей, которое будет перенесено ниже. Следующие три строки настраивают различные части MVC: области, фильтры и маршруты. Пакеты заменяются статическими файлами в перенесенном приложении. В последней строке настраивается доступ к данным приложения, которое будет показано в следующем разделе.

Поскольку это приложение на самом деле не использует области, нет ничего делать, чтобы перенести вызов регистрации в области. Если приложению необходимо выполнить миграцию областей, [Документация укажет, как настроить области в ASP.NET Core](/aspnet/core/mvc/controllers/areas).

Вызов для регистрации глобальных фильтров вызывает вспомогательное приложение для `FilterConfig` класса в папке *App_Start* приложения:

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

Единственным атрибутом, добавленным в приложение, является фильтр MVC ASP.NET `HandleErrorAttribute` . Этот фильтр гарантирует, что при возникновении исключения в составе запроса отображаются действие и представление по умолчанию, а не сведения об исключении. В ASP.NET Core эти же функции выполняются по `UseExceptionHandler` промежуточного слоя. Подробные сообщения об ошибках по умолчанию не включены. Они должны быть настроены с использованием по `UseDeveloperExceptionPage` промежуточного слоя. Чтобы настроить такое поведение в соответствии с исходным приложением, необходимо добавить следующий код в начало `Configure` метода в *Startup. CS*:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

Это берет на себя единственный фильтр, используемый приложением Ешоп, и в данном случае он выполнялся с помощью встроенного по промежуточного слоя. Если у вас есть глобальные фильтры, которые должны быть настроены в приложении, это делается при добавлении MVC в `ConfigureServices` метод, который показан далее в этой главе.

Последняя часть логики, относящейся к MVC, которую необходимо перенести, — это маршруты приложения по умолчанию. Вызов `RouteConfig.RegisterRoutes(RouteTable.Routes)` метода передает таблицу маршрутов MVC в `RegisterRoutes` вспомогательный метод, где при запуске приложения выполняется следующий код:

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

Переводя этот код в построчную, первая строка настраивает поддержку для маршрутов атрибутов. Эта возможность встроена в ASP.NET Core, поэтому ее не нужно настраивать отдельно. Аналогично, файлы *{Resource}. axd* не используются с ASP.NET Core, поэтому нет необходимости пропускать такие маршруты. `MapRoute`Метод настраивает значение по умолчанию для MVC, в котором используется стандартный `{controller}/{action}/{id}` шаблон маршрута. Он также задает значения по умолчанию для этого шаблона, так что используется `CatalogController` контроллером по умолчанию, а `Index` метод является действием по умолчанию. Большие приложения часто содержат дополнительные вызовы для `MapRoute` настройки дополнительных маршрутов.

ASP.NET Core MVC поддерживает [обычную маршрутизацию и маршрутизацию атрибутов](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2). Обычная маршрутизация аналогична настройке таблицы маршрутов в `RegisterRoutes` приведенном выше методе. Чтобы настроить стандартную маршрутизацию с использованием маршрута по умолчанию, аналогичного используемому в приложении *ешоп* , добавьте следующий код в конец `Configure` метода в *Startup. CS*:

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> При использовании ASP.NET Core 3,0 и более поздних версий это значение изменяется на использование конечных точек. Чтобы начальный порт ASP.NET Core 2,2, это правильный синтаксис для сопоставления стандартных маршрутов.

После внесения этих изменений `Configure` метод почти выполняется. Метод исходного шаблона `app.Run` , который выводит *Hello World!* следует удалить. На этом этапе метод показан ниже:

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

Теперь пора настроить службы MVC, а затем оставшуюся часть поддержки внедрения зависимостей (DI) в приложении. До сих пор метод проекта *ешоппортед* `ConfigureServices` остается пустым. Теперь пора приступить к заполнению.

Сначала необходимо добавить ASP.NET Core MVC для правильной работы.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

Приведенный выше код является минимальной конфигурацией, необходимой для получения работоспособных компонентов MVC. Существует множество дополнительных функций, которые можно настроить на основе этого вызова (некоторые из которых подробно описаны далее в этой главе), но теперь для этого достаточно будет создать приложение. Теперь он правильно направляет запрос по умолчанию, но, поскольку мы еще не настроили DI, во время активации возникает ошибка `CatalogController` , поскольку реализация типа `ICatalogService` еще не предоставлена. Сейчас мы вернемся к настройке MVC. Сейчас выполним миграцию внедрения зависимостей приложения.

#### <a name="migrate-dependency-injection-configuration"></a>Миграция конфигурации внедрения зависимостей

Файл *Global. asax* исходного приложения определяет следующий метод, который вызывается при запуске приложения:

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

Этот код настраивает контейнер [Autofac](https://autofac.org/) , считывает параметр конфигурации, чтобы определить, следует ли использовать реальные или фиктивные данные, и передает этот параметр в модуль Autofac (находится в каталоге */модулес* приложения). К счастью, Autofac поддерживает .NET Core, поэтому модуль можно перенести напрямую. Скопируйте папку в новый проект и обновите пространство имен класса, и оно должно быть скомпилировано.

ASP.NET Core имеет встроенную поддержку внедрения зависимостей, но при необходимости можно с легкостью подключить сторонний контейнер, например Autofac. В этом случае, поскольку приложение уже настроено для использования Autofac, самым простым решением является поддержание его использования. Для этого `ConfigureServices` необходимо изменить сигнатуру метода, чтобы она возвращала `IServiceProvider` , а экземпляр контейнера Autofac должен быть настроен и возвращен из метода.

**Примечание.** В .NET Core 3,0 и более поздних версиях процесс интеграции стороннего контейнера внедрения изменился.

Часть настройки Autofac требует вызова `builder.Populate(services)` . Это расширение находится в `Autofac.Extensions.DependencyInjection` пакете NuGet, которое необходимо установить перед компиляцией кода.

После изменения `ConfigureServices` для настройки контейнера Autofac используется новый метод, как показано ниже:

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

Пока параметр для `useMockData` имеет значение `true` . Этот параметр будет считан из конфигурации через некоторое время. На этом этапе приложение компилируется и должно успешно загружаться при запуске, как показано на рис. 4-12.

![Рис. 4-12](media/Figure4-12.png)

**Рис. 4-12**. Перенесенное приложение *ешоп* , работающее локально с фиктивными данными.

#### <a name="migrate-app-settings"></a>Перенос параметров приложения

В ASP.NET Core используется новая [система конфигурации](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2), которая по умолчанию использует *appsettings.jsв* файле. При использовании `CreateDefaultBuilder` в *Program. CS* конфигурация по умолчанию уже настроена в приложении. Для доступа к конфигурации классы просто должны запросить его в своем конструкторе. `Startup`Класс не является исключением. Чтобы начать доступ к конфигурации в `Startup` и остальной части приложения, запросите экземпляр `IConfiguration` из своего конструктора:

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

Исходное приложение, на которое ссылаются параметры с помощью `ConfigurationManager.AppSettings` . Быстрый поиск всех ссылок этого термина дает набор параметров, необходимых для нового приложения. Существует только два:

- `UseMockData`
- `UseCustomizationData`

Если приложение имеет более сложную конфигурацию, особенно если он использует пользовательские разделы конфигурации, то, вероятно, потребуется создать и привязать объекты к разным частям конфигурации приложения. Затем доступ к этим типам можно получить с помощью [шаблона параметров](../../core/extensions/options.md). Однако, как отмечалось в упоминаемом документе, этот шаблон не должен использоваться в `ConfigureServices` . Вместо этого перенесенное приложение будет ссылаться на `UseMockData` значение конфигурации напрямую.

Сначала измените файл перенесенного приложения `appsettings.json` и добавьте два параметра в корневой каталог:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

Теперь измените, `ConfigureServices` чтобы получить доступ к `UseMockData` параметру из `Configuration` Свойства (где ранее мы установили значение `true` ):

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

На этом этапе параметр извлекается из конфигурации. Другой параметр, `UseCustomizationData` , используется `CatalogDBInitializer` классом. При первом переносе этого класса вы заносите в комментарий доступ к `ConfigurationManager.AppSettings["UseCustomizationData"]` . Пришло время изменить его, чтобы использовать ASP.NET Coreную конфигурацию. Измените конструктор следующим образом `CatalogDBInitializer` :

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

Любой доступ к конфигурации в веб-приложении следует изменить таким образом, чтобы использовать новый `IConfiguration` тип. Зависимости, которым требуется доступ к платформа .NET Framework конфигурации, могут включать такие параметры в файл *app.config* , добавленный в веб-проект. Зависимые проекты могут работать с `ConfigurationManager` параметрами доступа и не должны требовать изменений, если они уже используют этот подход. Однако, поскольку ASP.NET Core приложения выполняются как собственные исполняемые файлы, они не ссылаются на *web.config* , а не *app.config*. При переносе параметров из файла *web.config* устаревших приложений в новый файл *app.config* в приложении ASP.NET Core, компоненты, использующиеся `ConfigurationManager` для доступа к их параметрам, будут продолжать работать правильно.

Миграция приложения почти завершена. Единственная оставшаяся задача — конфигурация доступа к данным.
  
## <a name="data-access-considerations"></a>Рекомендации по доступу к данным

ASP.NET Core приложения, работающие на платформа .NET Framework, могут продолжать использовать Entity Framework (EF). При выполнении добавочной миграции получение приложения, работающего с EF 6, перед попыткой переноса доступа к данным для использования EF Core может быть целесообразным. Таким образом, все проблемы, связанные с миграцией приложения, можно определить и устранить до начала другого блока усилий по миграции.

Как только это происходит, Настройка EF 6 в примере миграции Ешоп не требует специальной работы, так как эта работа была выполнена в Autofac `ApplicationModule` . Единственная проблема заключается в том, что в настоящее время `CatalogDBContext` класс пытается считать строку подключения из *web.config*. Чтобы устранить эту эту необходимость, необходимо добавить сведения о подключении в *appsettings.js*. После этого строка подключения должна быть передана в `CatalogDBContext` момент ее создания.

Обновите *appsettings.jsв* , чтобы включить строку подключения. Полный файл указан здесь:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

Строка подключения должна быть передана в конструктор при `DbContext` создании. Так как экземпляры создаются с помощью Autofac, необходимо внести изменения в `ApplicationModule` . Измените модуль, чтобы в нем перестать в `connectionString` конструктор и назначить его полю. Затем измените регистрацию для `CatalogDBContext` , чтобы добавить строку подключения в качестве параметра:

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

Параметр также необходимо добавить в новую перегрузку конструктора `CatalogDBContext` :

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

Наконец, `ConfigureServices` необходимо прочитать строку подключения из `Config` и передать ее в экземпляр, `ApplicationModule` когда он его создает.

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

После выполнения этого кода приложение выполняется, как и раньше, подключаясь к базе данных SQL Server, когда `UseMockData` имеет значение `false` .

На этом этапе приложение может быть развернуто и запущено в рабочей среде, преобразованное в ASP.NET Core, но по-прежнему выполняется на платформа .NET Framework и EF 6. При необходимости можно выполнить миграцию приложения на .NET Core и Entity Framework Core, что обеспечит дополнительные преимущества, описанные в предыдущих главах. В этой документации, относящейся к Entity Framework, [сравниваются EF Core и EF 6](/ef/efcore-and-ef6/) и включает сетку, показывающую, какая библиотека поддерживает каждую десятку отдельных функций.

### <a name="migrate-to-entity-framework-core"></a>Переход на Entity Framework Core

При принятии решения о переходе на EF Core действия могут быть довольно простыми, особенно если в исходном приложении использовался подход к модели на основе кода. При [подготовке к порту от EF 6 до EF Core](/ef/efcore-and-ef6/porting/)проверьте доступность функций в целевой версии EF Core, которую вы будете использовать. Изучите документацию по [переносу и модели на основе EDMX, а](/ef/efcore-and-ef6/porting/port-edmx) также [переносу из модели на основе кода](/ef/efcore-and-ef6/porting/port-code).

Чтобы выполнить обновление до EF Core 2,2, необходимо добавить соответствующие пакеты NuGet и обновить пространства имен. Затем настройте способ передачи строки подключения в `DbContext` тип и способ их связывания для внедрения зависимостей.

EF Core добавляется в качестве ссылки на пакет в проект:

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

Ссылка на EF 6 удалена:

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

Компилятор сообщит об ошибках в `CatalogDBContext` и `CatalogDBInitializer` . `CatalogDbContext` необходимо удалить старые пространства имен и заменить их на `Microsoft.EntityFrameworkCore` . Его конструкторы можно удалить. `DbModelBuilder` следует заменить на `ModelBuilder` . Вспомогательные методы для настройки типов перемещаются в отдельные классы, реализующие `IEntityTypeConfiguration<T>` . Затем `CatalogDBContext` `OnModelCreating` метод класса просто превращается в:

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

К другим задействованным изменениям относятся:

- `HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` заменяется на `ValueGeneratedNever()`
- `HasRequired<T>` заменяется на `HasOne<T>`
- Установленный `Microsoft.EntityFrameworkCore.Relational` пакет
- Добавление конструктора для получения `CatalogDBContext` `DbContextOptions` и передачи его в базовый конструктор

Ниже приведен пример класса конфигурации для `CatalogType` .

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

`CatalogDBInitializer`И его базовый класс, `CreateDatabaseIfNotExists<T>` не совместимы с EF Core. Этот класс предназначен для создания и заполнения базы данных. При использовании EF Core будет [создана и удалена связанная база `DbContext` данных для](/ef/core/managing-schemas/ensure-created) с использованием следующих методов:

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

Заполнение данных в EF Core можно выполнить с помощью ручных скриптов или в составе конфигурации типа. Вместе с другими свойствами сущности начальные данные можно настроить в `IEntityTypeConfiguration` классах с помощью `builder.HasData()` . Исходное приложение загрузило начальные данные из CSV-файлов в каталоге *установки* . Учитывая, что существует всего несколько элементов, эти записи данных могут быть добавлены как часть конфигурации сущности. Этот подход хорошо подходит для уточняющих данных в таблицах, которые изменяются редко. Добавление следующего метода в `CatalogTypeConfig` `Configure` метод гарантирует, что связанные строки будут представлены при создании базы данных:

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

Исходное приложение включает `PreconfiguredData` класс, который включает данные для `CatalogBrand` и `CatalogType` , поэтому использование этого метода `HasData` сокращается до:

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

`CatalogItem`Данные также могут быть извлечены из `PreconfiguredData` , и при условии, что связанные с ними образы хранятся в системе управления версиями, это последняя таблица, необходимая для работы приложения. `CatalogDBInitializer`Класс можно удалить вместе со всеми ссылками на него. `CatalogItemHiLoGenerator`Класс и файлы SQL в `Infrastructure` каталоге также удаляются вместе со всеми ссылками на них (в `CatalogService` `ApplicationModule` ).

После удаления специальных классов ключевых генераторов для `CatalogItem` этот код удаляется из `CatalogItemConfig` :

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

После внесения этих изменений приложение ASP.NET Core строится, но еще не работает с EF Core, которое по-прежнему должно быть настроено для внедрения зависимостей. С EF Core самый простой способ ее настройки `ConfigureServices` :

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

Окончательная версия Autofac `ApplicationModule` настраивает только один тип в зависимости от того, настроено ли приложение для использования фиктивных данных:

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }

    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

Переданное приложение выполняется, но не отображает данные, если настроено использование нефиктивных данных. Начальные данные, добавленные с помощью `HasData` , вставляются только при применении миграции. Исходное приложение не использовало миграцию, и, если оно имелось, они не будут перенесены как есть. Лучший подход — начать с нового сценария миграции. Для этого добавьте ссылку на пакет для `Microsoft.EntityFrameworkCore.Design` и откройте окно терминала в корневом каталоге проекта. Далее выполните:

```dotnetcli
dotnet ef migrations add Initial
```

Удалите существующую базу данных *ешоппортед* , если она существует, а затем выполните команду:

```dotnetcli
dotnet ef database update
```

При этом создается и заполняется база данных. Теперь он готов к запуску, и в нем осталось несколько небольших обновлений.

## <a name="fix-all-todo-tasks"></a>Исправить все задачи TODO

Запуск перенесенного приложения на этом этапе показывает, что на странице не отображаются изображения. Это обусловлено тем, что `PictureUri` свойство объекта не `CatalogItem` задано. Просмотрев список элементов, `TODO` созданных с помощью **список задач** Visual Studio, это единственный элемент, который остается в `CatalogController` , с заметкой "ссылка на Pic из wwwroot". Рассматриваемый код:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

Самым простым исправлением является ссылка на общедоступные файлы образов в общедоступном каталоге *wwwroot/pics* . Эту задачу можно выполнить, заменив метод следующим кодом:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

После этого изменения при запуске приложения образы работают как прежде.

## <a name="additional-mvc-customizations"></a>Дополнительные настройки MVC

Приложение *ешоплегацимвк* довольно простое, поэтому настройка в контексте поведения MVC по умолчанию не требует много усилий. Однако, если необходимо настроить дополнительные компоненты MVC, такие как CORS, фильтры и ограничения маршрутов, обычно эти сведения предоставляются в `Startup.ConfigureServices` , где `UseMvc` вызывается. Например, в следующем листинге кода настраивается [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) и настраивается глобальный фильтр действий:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> Чтобы завершить настройку CORS, необходимо также вызвать `app.UseCors()` в `Configure` .

В подробных ASP.NET Core документах рассматриваются другие сложные сценарии, например добавление [пользовательских связывателей модели](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2), модулей форматирования и многое другое. Как правило, их можно применять к отдельному контроллеру или действию или глобально с помощью тех же параметров, что и в приведенном выше листинге кода.

## <a name="other-dependencies"></a>Другие зависимости

Зависимости, использующие платформа .NET Framework функции, которые имеют зависимость от устаревшей модели конфигурации, например тип клиента WCF и код трассировки, должны быть изменены при переносе. Вместо того, чтобы эти типы извлекать данные о конфигурации напрямую, их следует настроить в коде. Например, подключение к службе WCF, которая была настроена в *web.config* приложения ASP.NET для использования, `basicHttpBinding` может быть настроено программно с помощью следующего кода:

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

Вместо использования файлов конфигурации для его параметров клиенты WCF и другие типы платформа .NET Framework должны иметь свои параметры, указанные в коде. Эти типы, настроенные таким образом, могут продолжать работать в приложениях ASP.NET Core 2,2.

## <a name="references"></a>Ссылки

- [репозиторий eShopModernizing GitHub](https://github.com/dotnet-architecture/eShopModernizing)
- [Помощник по обновлению .NET](https://aka.ms/dotnet-upgrade-assistant)
- [API и ViewModels не должны ссылаться на модели предметной области](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [Промежуточное по страницы исключений разработчика](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [Углубленное углубление в EF Core Хасдата](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
>[Назад](more-migration-scenarios.md)
>[Вперед](deployment-scenarios.md)
