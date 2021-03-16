---
title: Критическое изменение. Пути к коду в кодировке UTF-7 устарели
description: Ознакомьтесь с критическим изменением .NET 5 в основных библиотеках .NET, где конструкторы UTF7 и UTF7Encoding теперь считаются устаревшими.
ms.date: 11/01/2020
ms.openlocfilehash: 7a0ba771e0fac2908ca37f16afb10118e1537161
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256989"
---
# <a name="utf-7-code-paths-are-obsolete"></a>Пути к коду в кодировке UTF-7 устарели

Кодировка UTF-7 больше не используется широко в приложениях, и многие спецификации теперь [запрещают использовать ее](https://security.stackexchange.com/a/68609/3573) при обмене. Кроме того, иногда она [служит вектором атаки](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) в приложениях, которые не предусматривают получение данных в этой кодировке. Корпорация Майкрософт предостерегает от использования класса <xref:System.Text.UTF7Encoding?displayProperty=nameWithType>, так как он не выполняет обнаружение ошибок.

Таким образом, свойство <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и конструкторы <xref:System.Text.UTF7Encoding.%23ctor%2A> теперь также считаются устаревшими. Кроме того, методы <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> и <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> больше не позволяют определять `UTF-7`.

## <a name="change-description"></a>Описание изменений

Ранее экземпляр кодировки UTF-7 можно было создать с помощью API <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>. Пример:

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

Кроме того, экземпляр, представляющий кодировку UTF-7, перечислялся методом <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType>, который перечисляет все зарегистрированные в системе экземпляры <xref:System.Text.Encoding>.

Начиная с .NET 5, свойство <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и конструкторы <xref:System.Text.UTF7Encoding.%23ctor%2A> являются устаревшими и выдают предупреждение `SYSLIB0001` (или `MSLIB0001` в предварительных версиях). Но чтобы уменьшить число предупреждений, получаемых вызывающими объектами при использовании класса <xref:System.Text.UTF7Encoding>, сам тип <xref:System.Text.UTF7Encoding> не помечен как устаревший.

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

Кроме того, методы <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> интерпретируют имя кодировки `utf-7` и кодовую страницу `65000` как `unknown`. Получение значения `unknown` для кодировки вызывает исключение <xref:System.ArgumentException>.

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

Наконец, метод <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> не включает кодировку UTF-7 в возвращаемый массив <xref:System.Text.EncodingInfo>. Кодировка исключается, так как нельзя создать ее экземпляр.

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a>Причина изменения

Многие приложения вызывают метод `Encoding.GetEncoding("encoding-name")` с именем кодировки, полученным от ненадежного источника. Например, веб-клиент или сервер может взять фрагмент `charset` из заголовка `Content-Type` и передать его значение непосредственно в `Encoding.GetEncoding` без проверки. Это позволяет вредоносной конечной точке указать `Content-Type: ...; charset=utf-7`, что может привести к сбою принимающего приложения.

Кроме того, отключение путей к коду в UTF-7 позволяет оптимизировать работу компиляторов, например используемых в Blazor. При этом такие пути к коду полностью удаляются из полученного приложения. В результате скомпилированные приложения работают более эффективно и занимают меньше места на диске.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

В большинстве случаев никаких дополнительных действий от вас не требуется. Но если в приложении ранее были активированы пути к коду в UTF-7, воспользуйтесь приведенными ниже рекомендациями.

- Если приложение вызывает метод <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> с неизвестными именами кодировки, полученными от ненадежного источника:

  Вместо этого рекомендуется выполнять проверку имен кодировки по списку разрешенных. Этот настраиваемый список разрешенных кодировок должен по меньшей мере содержать стандартную отраслевую кодировку UTF-8. В зависимости от потребностей ваших клиентов и нормативных требований вам может также понадобится разрешить кодировки для определенных регионов, например GB18030.

  Если вы не создадите список разрешенных кодировок, метод <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> будет возвращать все значения <xref:System.Text.Encoding>, которые встроены в систему или зарегистрированы с помощью настраиваемого класса <xref:System.Text.EncodingProvider>. Проверьте требования службы, чтобы убедиться, что такое поведение допустимо. По умолчанию кодировка UTF-7 остается отключенной, если только приложение не включит параметр совместимости, упомянутый далее в этой статье.

- Если вы используете <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> или <xref:System.Text.UTF7Encoding> в своем формате протокола или файла:

  Перейдите на использование <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> или <xref:System.Text.UTF8Encoding>. Кодировка UTF-8 является отраслевым стандартом, поддерживающим различные языки, операционные системы и среды выполнения. Использование UTF-8 упрощает дальнейшее обслуживание кода и улучшает его совместимость с остальной экосистемой.

- Если вы сравниваете экземпляр <xref:System.Text.Encoding> со свойством <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:

  Вместо этого рекомендуется выполнять проверку по кодовой странице UTF-7 — `65000`. Сравнение с кодовой страницей позволяет избежать предупреждения, а также обрабатывать некоторые пограничные случаи, например, когда вызывается `new UTF7Encoding()` или создается подкласс типа.

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- Если вам необходимо использовать <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> или <xref:System.Text.UTF7Encoding>:

  Вы можете отключить предупреждение `SYSLIB0001` в коде или в файле *.csproj* проекта.

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > При подавлении `SYSLIB0001` отключаются только предупреждения о том, что <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и <xref:System.Text.UTF7Encoding> являются устаревшими. Это не отключает другие предупреждения и не меняет поведение API-интерфейсов, например <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.

- Если требуется поддержка `Encoding.GetEncoding("utf-7", ...)`:

  Вы можете повторно включить поддержку этой кодировки с помощью переключателя совместимости. Этот переключатель совместимости можно указать в файле *.csproj* приложения или [файле конфигурации среды выполнения](../../../run-time-config/index.md), как показано в следующих примерах.

  В файле *.csproj* приложения:

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  В файле *runtimeconfig.template.json*:

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > При повторном включении поддержки UTF-7 следует выполнить проверку безопасности кода, который вызывает <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
