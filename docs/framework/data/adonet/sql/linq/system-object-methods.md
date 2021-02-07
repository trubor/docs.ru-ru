---
description: Дополнительные сведения о методах System. Object
title: Методы System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 88ba4cf7cfc7dc9bea565b4689f77d088d424c44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681322"
---
# <a name="systemobject-methods"></a><span data-ttu-id="79e7e-103">Методы System.Object</span><span class="sxs-lookup"><span data-stu-id="79e7e-103">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="79e7e-104">поддерживает следующие <xref:System.Object> методы.</span><span class="sxs-lookup"><span data-stu-id="79e7e-104">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="79e7e-105">не поддерживает следующие методы <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="79e7e-105">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="79e7e-106"><xref:System.Object.ToString?displayProperty=nameWithType> для двоичных типов, таких как `BINARY`, `VARBINARY`, `IMAGE` и `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="79e7e-106"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="79e7e-107">Отличия от платформы .NET</span><span class="sxs-lookup"><span data-stu-id="79e7e-107">Differences from .NET</span></span>  

 <span data-ttu-id="79e7e-108">Выходные данные <xref:System.Object.ToString?displayProperty=nameWithType> для типа Double используют SQL `CONVERT` (nvarchar (30), @x , 2) в SQL.</span><span class="sxs-lookup"><span data-stu-id="79e7e-108">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="79e7e-109">В этом случае SQL всегда использует 16 цифр и экспоненциальный формат (например, «0.000000000000000e+000» для 0).</span><span class="sxs-lookup"><span data-stu-id="79e7e-109">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="79e7e-110">В результате преобразование <xref:System.Object.ToString?displayProperty=nameWithType> формирует строку, отличную от строки преобразования <xref:System.Convert.ToString%2A?displayProperty=nameWithType> на платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79e7e-110">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e7e-111">См. также</span><span class="sxs-lookup"><span data-stu-id="79e7e-111">See also</span></span>

- [<span data-ttu-id="79e7e-112">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="79e7e-112">Data Types and Functions</span></span>](data-types-and-functions.md)
