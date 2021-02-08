---
description: 'Дополнительные сведения о методе: Склстреамчарс. Write (char [], Int32, Int32)'
title: Метод Склстреамчарс. Write (char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3031b57902215df01c5c30625281a99be73ba2d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802558"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="bad5e-103">Метод Склстреамчарс. Write (char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="bad5e-103">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="bad5e-104">При переопределении в производном классе записывает последовательность символов в текущий поток и перемещает текущую позицию в этом потоке вперед на число записанных символов.</span><span class="sxs-lookup"><span data-stu-id="bad5e-104">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="bad5e-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="bad5e-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="bad5e-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bad5e-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="bad5e-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="bad5e-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="bad5e-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="bad5e-108">Parameters</span></span>

`buffer`  
<span data-ttu-id="bad5e-109">Массив символов для записи.</span><span class="sxs-lookup"><span data-stu-id="bad5e-109">A char array to write.</span></span>

`offset`  
<span data-ttu-id="bad5e-110">Смещение относительно начала координат.</span><span class="sxs-lookup"><span data-stu-id="bad5e-110">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="bad5e-111">Число символов, записываемых в текущий поток.</span><span class="sxs-lookup"><span data-stu-id="bad5e-111">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="bad5e-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="bad5e-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bad5e-113">`SqlStreamChars.Write`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="bad5e-113">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bad5e-114">Корпорация Майкрософт не поддерживает использование этого метода для написания в рабочем приложении каких-либо обстоятельств.</span><span class="sxs-lookup"><span data-stu-id="bad5e-114">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bad5e-115">Требования</span><span class="sxs-lookup"><span data-stu-id="bad5e-115">Requirements</span></span>

<span data-ttu-id="bad5e-116">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="bad5e-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="bad5e-117">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="bad5e-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="bad5e-118">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="bad5e-118">**.NET Framework versions:** Available since 2.0.</span></span>
