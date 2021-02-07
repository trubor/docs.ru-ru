---
description: 'Дополнительные сведения о методе: Склстреамчарс. Flush'
title: Метод Склстреамчарс. Flush (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f519ffb8248a17608319eb0fbfe598f9ee3487a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684468"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="c29cc-103">Склстреамчарс. Flush, метод</span><span class="sxs-lookup"><span data-stu-id="c29cc-103">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="c29cc-104">При переопределении в производном классе очищает все буферы данного потока и вызывает запись данных буферов в базовое устройство.</span><span class="sxs-lookup"><span data-stu-id="c29cc-104">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="c29cc-105">Сборка, содержащая этот метод, имеет дружественную связь с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="c29cc-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="c29cc-106">Он предназначен для использования SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c29cc-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="c29cc-107">Для других баз данных используйте механизм размещения, предоставляемый этой базой данных.</span><span class="sxs-lookup"><span data-stu-id="c29cc-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="c29cc-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c29cc-108">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="c29cc-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c29cc-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c29cc-110">`SqlStreamChars.Flush`Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="c29cc-110">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c29cc-111">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="c29cc-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c29cc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c29cc-112">Requirements</span></span>

<span data-ttu-id="c29cc-113">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="c29cc-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="c29cc-114">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="c29cc-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="c29cc-115">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="c29cc-115">**.NET Framework versions:** Available since 2.0.</span></span>
