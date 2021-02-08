---
description: Дополнительные сведения о свойстве Склстреамчарс. length
title: Склстреамчарс. length, свойство (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b0a9686cadc6d4018c7f291f0326b71195fd5cf5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802597"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="45ef8-103">Склстреамчарс. length, свойство</span><span class="sxs-lookup"><span data-stu-id="45ef8-103">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="45ef8-104">При переопределении в производном классе получает длину текущего потока.</span><span class="sxs-lookup"><span data-stu-id="45ef8-104">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="45ef8-105">Сборка, содержащая это свойство, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="45ef8-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="45ef8-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="45ef8-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="45ef8-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="45ef8-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="45ef8-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45ef8-108">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="45ef8-109">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="45ef8-109">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="45ef8-110">Длина потока.</span><span class="sxs-lookup"><span data-stu-id="45ef8-110">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="45ef8-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="45ef8-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="45ef8-112">`SqlStreamChars.Length`Свойство является закрытым и не предназначено для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="45ef8-112">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="45ef8-113">Корпорация Майкрософт не поддерживает использование этого свойства в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="45ef8-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="45ef8-114">Требования</span><span class="sxs-lookup"><span data-stu-id="45ef8-114">Requirements</span></span>

<span data-ttu-id="45ef8-115">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="45ef8-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="45ef8-116">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="45ef8-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="45ef8-117">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="45ef8-117">**.NET Framework versions:** Available since 2.0.</span></span>
