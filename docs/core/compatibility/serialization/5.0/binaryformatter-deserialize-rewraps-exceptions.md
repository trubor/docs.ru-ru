---
title: Критическое изменение. BinaryFormatter.Deserialize повторно изолирует некоторые исключения
description: Сведения о критическом изменении в .NET 5, где BinaryFormatter.Deserialize повторно изолирует некоторые объекты исключения в классе SerializationException.
ms.date: 08/18/2020
ms.openlocfilehash: 8e357035908f34c6c5c77d2a0728ab213bdc791a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256352"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="709df-103">Метод BinaryFormatter.Deserialize повторно изолирует некоторые исключения в классе SerializationException</span><span class="sxs-lookup"><span data-stu-id="709df-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="709df-104">Метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> теперь заключает некоторые объекты исключений в <xref:System.Runtime.Serialization.SerializationException> перед передачей исключения обратно вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="709df-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="709df-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="709df-105">Change description</span></span>

<span data-ttu-id="709df-106">Ранее метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> позволял использовать некоторые произвольные исключения, например <xref:System.ArgumentNullException>, для передачи стека соответствующим вызывающим объектам.</span><span class="sxs-lookup"><span data-stu-id="709df-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="709df-107">В .NET 5 и более поздних версиях метод <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> более агрессивно перехватывает исключения, вызываемые из-за недопустимых операций десериализации, и заключает их в <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="709df-107">In .NET 5 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="709df-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="709df-108">Version introduced</span></span>

<span data-ttu-id="709df-109">5.0</span><span class="sxs-lookup"><span data-stu-id="709df-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="709df-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="709df-110">Recommended action</span></span>

<span data-ttu-id="709df-111">В большинстве случаев никаких дополнительных действий от вас не требуется.</span><span class="sxs-lookup"><span data-stu-id="709df-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="709df-112">Но если место вызова зависит от конкретного исключения, вы можете исключить его из <xref:System.Runtime.Serialization.SerializationException>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="709df-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="709df-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="709df-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
