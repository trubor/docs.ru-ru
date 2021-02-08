---
description: 'Дополнительные сведения о методе: Склстреамчарс. SetLength (Int64)'
title: Метод Склстреамчарс. SetLength (Int64) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d10ce55126ae09062fe895c3a686ce5d94174554
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804144"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="0f659-103">Склстреамчарс. SetLength (Int64), метод</span><span class="sxs-lookup"><span data-stu-id="0f659-103">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="0f659-104">При переопределении в производном классе освобождает ресурсы, используемые потоком.</span><span class="sxs-lookup"><span data-stu-id="0f659-104">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="0f659-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="0f659-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0f659-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f659-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0f659-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="0f659-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="0f659-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f659-108">Parameters</span></span>

`value`\
<span data-ttu-id="0f659-109">Нужная длина текущего потока в байтах.</span><span class="sxs-lookup"><span data-stu-id="0f659-109">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f659-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f659-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0f659-111">`SqlStreamChars.SetLength`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="0f659-111">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0f659-112">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="0f659-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f659-113">Требования</span><span class="sxs-lookup"><span data-stu-id="0f659-113">Requirements</span></span>

<span data-ttu-id="0f659-114">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0f659-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0f659-115">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="0f659-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0f659-116">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="0f659-116">**.NET Framework versions:** Available since 2.0.</span></span>
