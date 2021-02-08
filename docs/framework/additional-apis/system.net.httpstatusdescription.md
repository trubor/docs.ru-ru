---
description: 'Дополнительные сведения о: Хттпстатусдескриптион Class'
title: Класс Хттпстатусдескриптион (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa135a6421397ce6b7be2af05d66aa8e81beafb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802506"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="236ce-103">Класс HttpStatusDescription</span><span class="sxs-lookup"><span data-stu-id="236ce-103">HttpStatusDescription class</span></span>

<span data-ttu-id="236ce-104">Предоставляет стандартные описания состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="236ce-104">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="236ce-105">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="236ce-105">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="236ce-106">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="236ce-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="236ce-107">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="236ce-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="236ce-108">Get - метод</span><span class="sxs-lookup"><span data-stu-id="236ce-108">Get method</span></span>

<span data-ttu-id="236ce-109">Возвращает описание, связанное с указанным кодом состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="236ce-109">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="236ce-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="236ce-110">Parameters</span></span>

<span data-ttu-id="236ce-111">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="236ce-111">`code` <xref:System.Int32></span></span>

<span data-ttu-id="236ce-112">Код состояния HTTP, например `404` .</span><span class="sxs-lookup"><span data-stu-id="236ce-112">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="236ce-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="236ce-113">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="236ce-114">Описание состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="236ce-114">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="236ce-115">Требования</span><span class="sxs-lookup"><span data-stu-id="236ce-115">Requirements</span></span>

<span data-ttu-id="236ce-116">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="236ce-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="236ce-117">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="236ce-117">**Assembly:** System (in System.dll)</span></span>
