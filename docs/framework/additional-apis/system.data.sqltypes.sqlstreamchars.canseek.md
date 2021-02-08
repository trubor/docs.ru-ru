---
description: 'Дополнительные сведения о свойстве: Склстреамчарс. CanSeek'
title: Свойство Склстреамчарс. CanSeek (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5919a66bef9ac31e0ef15ad4af64b456700605f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802623"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="a4cfb-103">Склстреамчарс. CanSeek, свойство</span><span class="sxs-lookup"><span data-stu-id="a4cfb-103">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="a4cfb-104">При переопределении в производном классе получает значение, указывающее, поддерживает ли текущий Steam операцию Seek.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-104">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="a4cfb-105">Сборка, содержащая это свойство, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a4cfb-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="a4cfb-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="a4cfb-108">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="a4cfb-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="a4cfb-109">`true` значение, если текущий Steam поддерживает операцию Seek; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a4cfb-109">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4cfb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="a4cfb-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a4cfb-111">`SqlStreamChars.CanSeek`Свойство является закрытым и не предназначено для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-111">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a4cfb-112">Корпорация Майкрософт не поддерживает использование этого свойства в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4cfb-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a4cfb-113">Requirements</span></span>

<span data-ttu-id="a4cfb-114">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a4cfb-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a4cfb-115">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="a4cfb-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a4cfb-116">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="a4cfb-116">**.NET Framework versions:** Available since 2.0.</span></span>
