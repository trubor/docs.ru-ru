---
description: 'Дополнительные сведения о свойстве: Склстреамчарс. IsNull'
title: Свойство Склстреамчарс. IsNull (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b1408a8ba9cd1c38f73d5fa6b818f441d6223bc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791924"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="4356a-103">Склстреамчарс. IsNull, свойство</span><span class="sxs-lookup"><span data-stu-id="4356a-103">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="4356a-104">При переопределении в производном классе получает значение, указывающее, является ли поток `null` .</span><span class="sxs-lookup"><span data-stu-id="4356a-104">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="4356a-105">Сборка, содержащая это свойство, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="4356a-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="4356a-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4356a-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="4356a-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="4356a-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="4356a-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4356a-108">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="4356a-109">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="4356a-109">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="4356a-110">`true` значение, если поток `null` ; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="4356a-110">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4356a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="4356a-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4356a-112">`SqlStreamChars.IsNull`Свойство является закрытым и не предназначено для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="4356a-112">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4356a-113">Корпорация Майкрософт не поддерживает использование этого свойства в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="4356a-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4356a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="4356a-114">Requirements</span></span>

<span data-ttu-id="4356a-115">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="4356a-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="4356a-116">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="4356a-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="4356a-117">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="4356a-117">**.NET Framework versions:** Available since 2.0.</span></span>
