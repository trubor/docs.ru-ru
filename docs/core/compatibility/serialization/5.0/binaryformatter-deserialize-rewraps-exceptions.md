---
title: Критическое изменение. BinaryFormatter.Deserialize повторно изолирует некоторые исключения
description: Сведения о критическом изменении в .NET 5.0, где BinaryFormatter.Deserialize повторно изолирует некоторые объекты исключения в классе SerializationException.
ms.date: 08/18/2020
ms.openlocfilehash: 90dc4cce6785fdb38644cca2a2e9aff65eb7a313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759685"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="007e9-103">Метод BinaryFormatter.Deserialize повторно изолирует некоторые исключения в классе SerializationException</span><span class="sxs-lookup"><span data-stu-id="007e9-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="007e9-104">Метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> теперь заключает некоторые объекты исключений в <xref:System.Runtime.Serialization.SerializationException> перед передачей исключения обратно вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="007e9-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="007e9-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="007e9-105">Change description</span></span>

<span data-ttu-id="007e9-106">Ранее метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> позволял использовать некоторые произвольные исключения, например <xref:System.ArgumentNullException>, для передачи стека соответствующим вызывающим объектам.</span><span class="sxs-lookup"><span data-stu-id="007e9-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="007e9-107">В .NET 5.0 и более поздних версиях метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> более агрессивно перехватывает исключения, вызываемые из-за недопустимых операций десериализации, и заключает их в <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="007e9-107">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="007e9-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="007e9-108">Version introduced</span></span>

<span data-ttu-id="007e9-109">5.0</span><span class="sxs-lookup"><span data-stu-id="007e9-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="007e9-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="007e9-110">Recommended action</span></span>

<span data-ttu-id="007e9-111">В большинстве случаев никаких дополнительных действий от вас не требуется.</span><span class="sxs-lookup"><span data-stu-id="007e9-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="007e9-112">Но если место вызова зависит от конкретного исключения, вы можете исключить его из <xref:System.Runtime.Serialization.SerializationException>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="007e9-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a><span data-ttu-id="007e9-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="007e9-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
