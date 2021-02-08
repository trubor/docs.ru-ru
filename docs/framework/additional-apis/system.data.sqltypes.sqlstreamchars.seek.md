---
description: 'Дополнительные сведения о методе: Склстреамчарс. Seek (Int64, SeekOrigin)'
title: Метод Склстреамчарс. Seek (Int64, SeekOrigin) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 00f71aff95045d566b7932aec3f7e18259b4dfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802571"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="32f11-103">Метод Склстреамчарс. Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="32f11-103">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="32f11-104">При переопределении в производном классе задает позицию в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="32f11-104">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="32f11-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="32f11-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="32f11-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="32f11-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="32f11-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="32f11-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="32f11-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="32f11-108">Parameters</span></span>

`offset`\
<span data-ttu-id="32f11-109">Смещение в байтах относительно `origin`.</span><span class="sxs-lookup"><span data-stu-id="32f11-109">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="32f11-110">Одно из значений перечисления, указывающее точку ссылки, из которой следует получить новую позицию.</span><span class="sxs-lookup"><span data-stu-id="32f11-110">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="32f11-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="32f11-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="32f11-112">Новая позиция в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="32f11-112">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="32f11-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="32f11-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="32f11-114">`SqlStreamChars.Seek`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="32f11-114">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="32f11-115">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="32f11-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="32f11-116">Требования</span><span class="sxs-lookup"><span data-stu-id="32f11-116">Requirements</span></span>

<span data-ttu-id="32f11-117">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="32f11-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="32f11-118">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="32f11-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="32f11-119">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="32f11-119">**.NET Framework versions:** Available since 2.0.</span></span>
