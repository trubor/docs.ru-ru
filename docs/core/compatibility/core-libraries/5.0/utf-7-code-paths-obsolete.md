---
title: Критическое изменение. Пути к коду в кодировке UTF-7 устарели
description: Ознакомьтесь с критическим изменением .NET 5.0 в основных библиотеках .NET, где конструкторы UTF7 и UTF7Encoding теперь считаются устаревшими.
ms.date: 11/01/2020
ms.openlocfilehash: d58305f59a30cdf31a525c3789bd6497201c50ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759654"
---
# <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="da1e1-103">Пути к коду в кодировке UTF-7 устарели</span><span class="sxs-lookup"><span data-stu-id="da1e1-103">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="da1e1-104">Кодировка UTF-7 больше не используется широко в приложениях, и многие спецификации теперь [запрещают использовать ее](https://security.stackexchange.com/a/68609/3573) при обмене.</span><span class="sxs-lookup"><span data-stu-id="da1e1-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="da1e1-105">Кроме того, иногда она [служит вектором атаки](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) в приложениях, которые не предусматривают получение данных в этой кодировке.</span><span class="sxs-lookup"><span data-stu-id="da1e1-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="da1e1-106">Корпорация Майкрософт предостерегает от использования класса <xref:System.Text.UTF7Encoding?displayProperty=nameWithType>, так как он не выполняет обнаружение ошибок.</span><span class="sxs-lookup"><span data-stu-id="da1e1-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="da1e1-107">Таким образом, свойство <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и конструкторы <xref:System.Text.UTF7Encoding.%23ctor%2A> теперь также считаются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="da1e1-107">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="da1e1-108">Кроме того, методы <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> и <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> больше не позволяют определять `UTF-7`.</span><span class="sxs-lookup"><span data-stu-id="da1e1-108">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

## <a name="change-description"></a><span data-ttu-id="da1e1-109">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="da1e1-109">Change description</span></span>

<span data-ttu-id="da1e1-110">Ранее экземпляр кодировки UTF-7 можно было создать с помощью API <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-110">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="da1e1-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="da1e1-111">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="da1e1-112">Кроме того, экземпляр, представляющий кодировку UTF-7, перечислялся методом <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType>, который перечисляет все зарегистрированные в системе экземпляры <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-112">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="da1e1-113">Начиная с .NET 5.0, свойство <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и конструкторы <xref:System.Text.UTF7Encoding.%23ctor%2A> являются устаревшими и выдают предупреждение `SYSLIB0001` (или `MSLIB0001` в предварительных версиях).</span><span class="sxs-lookup"><span data-stu-id="da1e1-113">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="da1e1-114">Но чтобы уменьшить число предупреждений, получаемых вызывающими объектами при использовании класса <xref:System.Text.UTF7Encoding>, сам тип <xref:System.Text.UTF7Encoding> не помечен как устаревший.</span><span class="sxs-lookup"><span data-stu-id="da1e1-114">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="da1e1-115">Кроме того, методы <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> интерпретируют имя кодировки `utf-7` и кодовую страницу `65000` как `unknown`.</span><span class="sxs-lookup"><span data-stu-id="da1e1-115">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="da1e1-116">Получение значения `unknown` для кодировки вызывает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-116">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="da1e1-117">Наконец, метод <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> не включает кодировку UTF-7 в возвращаемый массив <xref:System.Text.EncodingInfo>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-117">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="da1e1-118">Кодировка исключается, так как нельзя создать ее экземпляр.</span><span class="sxs-lookup"><span data-stu-id="da1e1-118">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a><span data-ttu-id="da1e1-119">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="da1e1-119">Reason for change</span></span>

<span data-ttu-id="da1e1-120">Многие приложения вызывают метод `Encoding.GetEncoding("encoding-name")` с именем кодировки, полученным от ненадежного источника.</span><span class="sxs-lookup"><span data-stu-id="da1e1-120">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="da1e1-121">Например, веб-клиент или сервер может взять фрагмент `charset` из заголовка `Content-Type` и передать его значение непосредственно в `Encoding.GetEncoding` без проверки.</span><span class="sxs-lookup"><span data-stu-id="da1e1-121">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="da1e1-122">Это позволяет вредоносной конечной точке указать `Content-Type: ...; charset=utf-7`, что может привести к сбою принимающего приложения.</span><span class="sxs-lookup"><span data-stu-id="da1e1-122">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="da1e1-123">Кроме того, отключение путей к коду в UTF-7 позволяет оптимизировать работу компиляторов, например используемых в Blazor. При этом такие пути к коду полностью удаляются из полученного приложения.</span><span class="sxs-lookup"><span data-stu-id="da1e1-123">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="da1e1-124">В результате скомпилированные приложения работают более эффективно и занимают меньше места на диске.</span><span class="sxs-lookup"><span data-stu-id="da1e1-124">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="da1e1-125">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="da1e1-125">Version introduced</span></span>

<span data-ttu-id="da1e1-126">5.0</span><span class="sxs-lookup"><span data-stu-id="da1e1-126">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="da1e1-127">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="da1e1-127">Recommended action</span></span>

<span data-ttu-id="da1e1-128">В большинстве случаев никаких дополнительных действий от вас не требуется.</span><span class="sxs-lookup"><span data-stu-id="da1e1-128">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="da1e1-129">Но если в приложении ранее были активированы пути к коду в UTF-7, воспользуйтесь приведенными ниже рекомендациями.</span><span class="sxs-lookup"><span data-stu-id="da1e1-129">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="da1e1-130">Если приложение вызывает метод <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> с неизвестными именами кодировки, полученными от ненадежного источника:</span><span class="sxs-lookup"><span data-stu-id="da1e1-130">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="da1e1-131">Вместо этого рекомендуется выполнять проверку имен кодировки по списку разрешенных.</span><span class="sxs-lookup"><span data-stu-id="da1e1-131">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="da1e1-132">Этот настраиваемый список разрешенных кодировок должен по меньшей мере содержать стандартную отраслевую кодировку UTF-8.</span><span class="sxs-lookup"><span data-stu-id="da1e1-132">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="da1e1-133">В зависимости от потребностей ваших клиентов и нормативных требований вам может также понадобится разрешить кодировки для определенных регионов, например GB18030.</span><span class="sxs-lookup"><span data-stu-id="da1e1-133">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="da1e1-134">Если вы не создадите список разрешенных кодировок, метод <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> будет возвращать все значения <xref:System.Text.Encoding>, которые встроены в систему или зарегистрированы с помощью настраиваемого класса <xref:System.Text.EncodingProvider>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-134">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="da1e1-135">Проверьте требования службы, чтобы убедиться, что такое поведение допустимо.</span><span class="sxs-lookup"><span data-stu-id="da1e1-135">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="da1e1-136">По умолчанию кодировка UTF-7 остается отключенной, если только приложение не включит параметр совместимости, упомянутый далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="da1e1-136">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="da1e1-137">Если вы используете <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> или <xref:System.Text.UTF7Encoding> в своем формате протокола или файла:</span><span class="sxs-lookup"><span data-stu-id="da1e1-137">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="da1e1-138">Перейдите на использование <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> или <xref:System.Text.UTF8Encoding>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-138">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="da1e1-139">Кодировка UTF-8 является отраслевым стандартом, поддерживающим различные языки, операционные системы и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="da1e1-139">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="da1e1-140">Использование UTF-8 упрощает дальнейшее обслуживание кода и улучшает его совместимость с остальной экосистемой.</span><span class="sxs-lookup"><span data-stu-id="da1e1-140">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="da1e1-141">Если вы сравниваете экземпляр <xref:System.Text.Encoding> со свойством <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="da1e1-141">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="da1e1-142">Вместо этого рекомендуется выполнять проверку по кодовой странице UTF-7 — `65000`.</span><span class="sxs-lookup"><span data-stu-id="da1e1-142">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="da1e1-143">Сравнение с кодовой страницей позволяет избежать предупреждения, а также обрабатывать некоторые пограничные случаи, например, когда вызывается `new UTF7Encoding()` или создается подкласс типа.</span><span class="sxs-lookup"><span data-stu-id="da1e1-143">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="da1e1-144">Если вам необходимо использовать <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> или <xref:System.Text.UTF7Encoding>:</span><span class="sxs-lookup"><span data-stu-id="da1e1-144">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="da1e1-145">Вы можете отключить предупреждение `SYSLIB0001` в коде или в файле *.csproj* проекта.</span><span class="sxs-lookup"><span data-stu-id="da1e1-145">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

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
  > <span data-ttu-id="da1e1-146">При подавлении `SYSLIB0001` отключаются только предупреждения о том, что <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> и <xref:System.Text.UTF7Encoding> являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="da1e1-146">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="da1e1-147">Это не отключает другие предупреждения и не меняет поведение API-интерфейсов, например <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-147">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="da1e1-148">Если требуется поддержка `Encoding.GetEncoding("utf-7", ...)`:</span><span class="sxs-lookup"><span data-stu-id="da1e1-148">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="da1e1-149">Вы можете повторно включить поддержку этой кодировки с помощью переключателя совместимости.</span><span class="sxs-lookup"><span data-stu-id="da1e1-149">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="da1e1-150">Этот переключатель совместимости можно указать в файле *.csproj* приложения или [файле конфигурации среды выполнения](../../../run-time-config/index.md), как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="da1e1-150">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="da1e1-151">В файле *.csproj* приложения:</span><span class="sxs-lookup"><span data-stu-id="da1e1-151">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="da1e1-152">В файле *runtimeconfig.template.json*:</span><span class="sxs-lookup"><span data-stu-id="da1e1-152">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="da1e1-153">При повторном включении поддержки UTF-7 следует выполнить проверку безопасности кода, который вызывает <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da1e1-153">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="da1e1-154">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="da1e1-154">Affected APIs</span></span>

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
