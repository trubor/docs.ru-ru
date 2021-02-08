---
description: 'Дополнительные сведения о методе: Склстреамчарс. Read (char [], Int32, Int32)'
title: Метод Склстреамчарс. Read (char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: a899ddff7b7242fcc32aaf7b7f7794970596027b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802584"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="a6379-103">Метод Склстреамчарс. Read (char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="a6379-103">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="a6379-104">При переопределении в производном классе считывает следующий набор символов из входного потока.</span><span class="sxs-lookup"><span data-stu-id="a6379-104">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="a6379-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="a6379-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a6379-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6379-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="a6379-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="a6379-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="a6379-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6379-108">Parameters</span></span>

`buffer`\
<span data-ttu-id="a6379-109">Массив символов для чтения.</span><span class="sxs-lookup"><span data-stu-id="a6379-109">A char array to read.</span></span>

`offset`\
<span data-ttu-id="a6379-110">Смещение относительно начала координат.</span><span class="sxs-lookup"><span data-stu-id="a6379-110">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="a6379-111">Число символов, считываемых из текущего потока.</span><span class="sxs-lookup"><span data-stu-id="a6379-111">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="a6379-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a6379-112">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="a6379-113">Общее количество символов, считанных в буфер.</span><span class="sxs-lookup"><span data-stu-id="a6379-113">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6379-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6379-114">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a6379-115">`SqlStreamChars.Read`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="a6379-115">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a6379-116">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="a6379-116">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6379-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a6379-117">Requirements</span></span>

<span data-ttu-id="a6379-118">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a6379-118">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a6379-119">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="a6379-119">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a6379-120">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6379-120">**.NET Framework versions:** Available since 2.0.</span></span>
