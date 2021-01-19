---
title: Критическое изменение. Методы сериализации BinaryFormatter устарели и запрещены в приложениях ASP.NET
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где методы сериализации и десериализации BinaryFormatter, Formatter и IFormatter устарели.
ms.date: 11/01/2020
ms.openlocfilehash: 1dca30d33f2aa0a6fe8f05fe728557092f836b2d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189848"
---
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="f679d-103">Методы сериализации BinaryFormatter устарели и запрещены в приложениях ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f679d-103">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="f679d-104">Методы `Serialize` и `Deserialize` в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter> и <xref:System.Runtime.Serialization.IFormatter> теперь считаются устаревшими и приводят к созданию предупреждения.</span><span class="sxs-lookup"><span data-stu-id="f679d-104">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete as warning.</span></span> <span data-ttu-id="f679d-105">Кроме того, сериализация <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> по умолчанию запрещена для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f679d-105">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

## <a name="change-description"></a><span data-ttu-id="f679d-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f679d-106">Change description</span></span>

<span data-ttu-id="f679d-107">Из-за [уязвимостей системы безопасности](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> следующие методы считаются устаревшими и во время компиляции приводят к созданию предупреждения с идентификатором `SYSLIB0011`.</span><span class="sxs-lookup"><span data-stu-id="f679d-107">Due to [security vulnerabilities](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete and produce a compile-time warning with ID `SYSLIB0011`.</span></span> <span data-ttu-id="f679d-108">Кроме того, в приложениях ASP.NET Core 5.0 и более поздних версий они вызовут исключение <xref:System.NotSupportedException>, если только веб-приложение не включило повторно функциональные возможности <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="f679d-108">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="f679d-109">Следующие методы сериализации также считаются устаревшими и приводят к созданию предупреждения `SYSLIB0011`, но изменений в их поведении не произошло:</span><span class="sxs-lookup"><span data-stu-id="f679d-109">The following serialization methods are also obsolete and produce warning `SYSLIB0011`, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a><span data-ttu-id="f679d-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f679d-110">Version introduced</span></span>

<span data-ttu-id="f679d-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f679d-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f679d-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="f679d-112">Reason for change</span></span>

<span data-ttu-id="f679d-113">Эти методы объявлены устаревшими в рамках мер по отказу от использования <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> в экосистеме .NET.</span><span class="sxs-lookup"><span data-stu-id="f679d-113">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f679d-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f679d-114">Recommended action</span></span>

- <span data-ttu-id="f679d-115">Не используйте в коде <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="f679d-115">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="f679d-116">Рассмотрите возможность использования <xref:System.Text.Json.JsonSerializer> или <xref:System.Xml.Serialization.XmlSerializer> вместо них.</span><span class="sxs-lookup"><span data-stu-id="f679d-116">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f679d-117">Дополнительные сведения см. в статье [Руководство по безопасности BinaryFormatter](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f679d-117">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="f679d-118">Можно временно отключить появляющееся во время компиляции предупреждение об использовании <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> (`SYSLIB0011`).</span><span class="sxs-lookup"><span data-stu-id="f679d-118">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="f679d-119">Перед этим мы рекомендуем тщательно оценить риски для кода.</span><span class="sxs-lookup"><span data-stu-id="f679d-119">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="f679d-120">Самый простой способ отключить предупреждения — обособить отдельные места вызова директивами `#pragma`.</span><span class="sxs-lookup"><span data-stu-id="f679d-120">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="f679d-121">Предупреждение можно также отключить в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="f679d-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="f679d-122">В этом случае предупреждение будет отключено во всех файлах с кодом в проекте.</span><span class="sxs-lookup"><span data-stu-id="f679d-122">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="f679d-123">Подавление `SYSLIB0011` не приводит к отключению предупреждений, вызванных использованием других устаревших API.</span><span class="sxs-lookup"><span data-stu-id="f679d-123">Suppressing `SYSLIB0011` does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="f679d-124">Чтобы продолжить использование <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> в приложениях ASP.NET, можно повторно включить их в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="f679d-124">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="f679d-125">Но делать это настоятельно не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="f679d-125">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="f679d-126">Дополнительные сведения см. в статье [Руководство по безопасности BinaryFormatter](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f679d-126">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="f679d-127">Дополнительные сведения о рекомендуемых действиях см. в статье [Устранение ошибок, связанных с устареванием и отключением BinaryFormatter](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f679d-127">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f679d-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f679d-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET Core

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
