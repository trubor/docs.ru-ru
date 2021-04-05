---
ms.openlocfilehash: b75f9ce8e878c935dcc5fd9dc292369720b895e9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105152728"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP. Изменения SameSite в браузере влияют на проверку подлинности

Для некоторых браузеров, таких как Chrome и Firefox, были внесены критические изменения в реализации `SameSite` для файлов cookie. Эти изменения негативно влияют на сценарии удаленной проверки подлинности, такие как OpenID Connect и WS-Federation, от которых нужно явно отказаться, отправив `SameSite=None`. Однако `SameSite=None` нарушает работу других браузеров в iOS 12 и некоторых более старых версий. Приложению требуется определить эти версии и опустить `SameSite`.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Представленная версия

3.1 (предварительная версия 1)

#### <a name="old-behavior"></a>Старое поведение

`SameSite` является расширением проекта стандарта за 2016 год для файлов cookie в HTTP. Этот атрибут предназначен для устранения подделки межсайтовых запросов (CSRF). Изначально этот атрибут был спроектирован в виде функции, с которой серверы должны были явно соглашаться, добавляя новые параметры. В ASP.NET Core 2.0 была добавлена начальная поддержка для `SameSite`.

#### <a name="new-behavior"></a>Новое поведение

Компания Google предложила новый проект стандарта, не имеющий обратной совместимости. Этот стандарт изменяет режим по умолчанию на `Lax` и добавляет новую запись `None` для явного отказа. `Lax` подходит для файлов cookie большинства приложений, однако нарушает работу межсайтовых сценариев, таких как вход с использованием WS-Federation и OpenID Connect. Основную часть процедур входа OAuth это не затрагивает из-за различий в последовательностях обработки запросов. Новый параметр `None` вызывает проблемы совместимости для клиентов, в которых реализован предыдущий проект стандарта (например, iOS 12). Эти изменения будут включены в Chrome 80. Сведения о сроках выпуска продукта Chrome см. в [новостях по SameSite](https://www.chromium.org/updates/same-site).

Продукт ASP.NET Core 3.1 был обновлен, чтобы реализовать новое поведение `SameSite`. Это обновление переопределяет поведение `SameSiteMode.None` для выдачи `SameSite=None` и добавляет новое значение `SameSiteMode.Unspecified`, чтобы опустить атрибут `SameSite`. Все API файлов cookie теперь по умолчанию используют `Unspecified`, хотя некоторые компоненты, использующие файлы cookie, задают более конкретные значения для соответствующих сценариев, таких как корреляция OpenID Connect и файлы cookie nonce.

Сведения о последних переменах в этой области см. в разделе [HTTP. Некоторые значения по умолчанию параметра SameSite для файлов cookie изменены на None](../../../../docs/core/compatibility/3.0.md#http-some-cookie-samesite-defaults-changed-to-none). В ASP.NET Core 3.0 большинство значений по умолчанию изменились с <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> на <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (однако по-прежнему используется более ранний стандарт).

#### <a name="reason-for-change"></a>Причина изменения

Изменения в браузере и спецификации, описанные выше.

#### <a name="recommended-action"></a>Рекомендованное действие

Приложения, взаимодействующие с удаленными сайтами, например через стороннюю процедуру входа, должны:

* тестировать эти сценарии в нескольких браузерах;
* применить исправление определения браузеров в рамках политики файлов cookie, описанное в разделе [Поддержка более старых браузеров](#support-older-browsers).

Инструкции по тестированию и определению браузеров см. в следующем разделе:

##### <a name="determine-if-youre-affected"></a>Определение того, затрагивают ли вас эти изменения

Протестируйте свое веб-приложение с использованием версии клиента, которая может явно согласиться на новое поведение. В Chrome, Firefox и Microsoft Edge Chromium предусмотрены флаги функции явного согласия, которые можно использовать для тестирования. Убедитесь, что ваше приложение совместимо с более старыми версиями клиента после установки исправлений, что особенно актуально для Safari. Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 и более поздних версий дает неверные результаты тестирования. Эти версии используют временные меры исправления и позволяют использовать файлы cookie, имеющие возраст менее двух минут. При включении соответствующих флагов тестирования Chrome 76 и 77 дают более точные результаты. Чтобы проверить новое поведение, включите `chrome://flags/#same-site-by-default-cookies`. Для Chrome 75 и более ранних версий новый параметр `None` вызывает ошибку. Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).

Google не предоставляет более старые версии Chrome. Однако можно скачать более старые версии Chromium, которых достаточно для тестирования. Следуйте указаниям на странице [скачивания Chromium](https://www.chromium.org/getting-involved/download-chromium).

* [Chromium 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chromium 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

В Safari 12 строго реализован предыдущий проект стандарта, поэтому этот браузер завершается со сбоем, если встречает новое значение `None` в файлах cookie. Такой сценарий следует исключить с помощью кода определения браузеров, приведенного в разделе [Поддержка более старых браузеров](#support-older-browsers). Обязательно проведите тестирование Safari 12 и 13, а также процедур входа на основе WebKit и механизмов ОС с использованием Библиотеки проверки подлинности Майкрософт (MSAL), Библиотеки проверки подлинности Active Directory (ADAL) или любой другой библиотеки. Эта проблема зависит от базовой версии ОС. Известно, что в OSX Mojave 10.14 и iOS 12 имеются проблемы совместимости с этим новым поведением. Обновление до OSX Catalina 10.15 или iOS 13 позволяет устранить их. Сейчас в Safari нет флага явного согласия для тестирования поведения, описанного в новой спецификации.

##### <a name="firefox"></a>Firefox

Поддержку нового стандарта для Firefox можно проверить в версии 68 и более поздних, указав явное согласие на странице `about:config` с помощью флага компонента `network.cookie.sameSite.laxByDefault`. Сведения о проблемах совместимости для более ранних версий Firefox отсутствуют.

##### <a name="microsoft-edge"></a>Microsoft Edge

Хотя Microsoft Edge поддерживает старый стандарт `SameSite`, начиная с версии 44, в нем нет никаких проблем совместимости с новым стандартом.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Chromium

Используется флаг компонента `edge://flags/#same-site-by-default-cookies`. При тестировании в Microsoft Chromium 78 никакие проблемы совместимости не наблюдались.

##### <a name="electron"></a>Electron

Версии Electron включают в себя более старые версии Chromium. Например, в Microsoft Teams используется версия Electron — Chromium 66, в которой реализовано старое поведение. Выполните собственное тестирование совместимости для версии Electron, используемой вашим продуктом. Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).

##### <a name="support-older-browsers"></a>Поддержка более старых браузеров

Стандарт `SameSite` за 2016 год предписывает обрабатывать неизвестные значения как значения `SameSite=Strict`. Следовательно, все старые браузеры, поддерживающие оригинальный стандарт, могут прекращать работу, встретив свойство `SameSite` со значением `None`. Если требуется поддерживать эти старые браузеры, веб-приложения должны реализовать определение браузеров. ASP.NET Core не реализует определение браузеров, так как значения заголовков запросов `User-Agent` крайне непостоянны и меняются каждую неделю. Вместо этого точка расширения в политике файлов cookie позволяет добавить логику, связанную с `User-Agent`.

Добавьте в файл *Startup.cs* следующий код:

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a>Параметры явного отказа

Параметр совместимости `Microsoft.AspNetCore.SuppressSameSiteNone` позволяет временно явно отказаться от нового поведения файлов cookie ASP.NET Core. Добавьте следующий код JSON в файл *runtimeconfig.template.json* в своем проекте:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Другие версии

Подготавливаются к выпуску соответствующие исправления `SameSite` для следующих продуктов:

* ASP.NET Core 2.1, 2.2 и 3.0
* `Microsoft.Owin` 4.1
* `System.Web` (для .NET Framework 4.7.2 и более поздних версий)

#### <a name="category"></a>Категория

ASP.NET

#### <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
