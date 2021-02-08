---
description: 'Дополнительные сведения о методе: Склстреамчарс. Dispose (Boolean)'
title: Метод Склстреамчарс. Dispose (Boolean) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ce24cc885d87a3ff0bbcdbea7992ca78ee592454
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802610"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="e8322-103">Метод Склстреамчарс. Dispose (логический)</span><span class="sxs-lookup"><span data-stu-id="e8322-103">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="e8322-104">При переопределении в производном классе освобождает ресурсы, используемые потоком.</span><span class="sxs-lookup"><span data-stu-id="e8322-104">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="e8322-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e8322-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e8322-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e8322-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e8322-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="e8322-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="e8322-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8322-108">Parameters</span></span>

`disposing`\
<span data-ttu-id="e8322-109">Значение `true` позволяет освободить как управляемые, так и неуправляемые ресурсы; значение `false` освобождает только неуправляемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="e8322-109">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8322-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8322-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e8322-111">`SqlStreamChars.Dispose`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="e8322-111">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e8322-112">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="e8322-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8322-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e8322-113">Requirements</span></span>

<span data-ttu-id="e8322-114">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e8322-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e8322-115">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e8322-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e8322-116">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="e8322-116">**.NET Framework versions:** Available since 2.0.</span></span>
