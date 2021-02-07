---
description: Дополнительные сведения о методах System. Math
title: Методы System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e97e0a16b6eafdb57f4aaf72d62788e6657afbdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681348"
---
# <a name="systemmath-methods"></a><span data-ttu-id="7de58-103">Методы System.Math</span><span class="sxs-lookup"><span data-stu-id="7de58-103">System.Math Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7de58-104">не поддерживает следующие методы <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="7de58-104">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="7de58-105">Отличия от платформы .NET</span><span class="sxs-lookup"><span data-stu-id="7de58-105">Differences from .NET</span></span>  

 <span data-ttu-id="7de58-106">Семантики округления в .NET Framework отличаются от подобных семантик SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7de58-106">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="7de58-107"><xref:System.Math.Round%2A>Метод в платформа .NET Framework выполняет *Округление банка*, где числа, заканчивающиеся на 0,5, округляются до ближайшей четной цифры, а не до следующей более высокой цифры.</span><span class="sxs-lookup"><span data-stu-id="7de58-107">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="7de58-108">Например, число 2,5 округляется до 2, а 3,5 - до 4.</span><span class="sxs-lookup"><span data-stu-id="7de58-108">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="7de58-109">(Это помогает избежать систематического смещения в сторону более высоких значений в транзакциях данных.)</span><span class="sxs-lookup"><span data-stu-id="7de58-109">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="7de58-110">В SQL, наоборот, функция `ROUND` всегда округляет от нуля.</span><span class="sxs-lookup"><span data-stu-id="7de58-110">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="7de58-111">Поэтому число 2,5 округляется до 3, тогда как в платформе .NET Framework - до 2.</span><span class="sxs-lookup"><span data-stu-id="7de58-111">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7de58-112">передается в семантики SQL `ROUND` и не пытается реализовать банковское округление.</span><span class="sxs-lookup"><span data-stu-id="7de58-112">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de58-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7de58-113">See also</span></span>

- [<span data-ttu-id="7de58-114">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="7de58-114">Data Types and Functions</span></span>](data-types-and-functions.md)
