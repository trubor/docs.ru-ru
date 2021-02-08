---
description: 'Дополнительные сведения: пространственные функции'
title: Пространственные функции
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: cde8f1b0fcf5904eb33fe061de69e566da2804dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767886"
---
# <a name="spatial-functions"></a><span data-ttu-id="778da-103">Пространственные функции</span><span class="sxs-lookup"><span data-stu-id="778da-103">Spatial Functions</span></span>

<span data-ttu-id="778da-104">Форматов литералов для пространственных типов не имеется.</span><span class="sxs-lookup"><span data-stu-id="778da-104">There is no literal format for spatial types.</span></span> <span data-ttu-id="778da-105">Однако можно использовать канонические функции Entity Framework, вызываемые с помощью строк в формате известного текстового представления.</span><span class="sxs-lookup"><span data-stu-id="778da-105">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="778da-106">Например, следующий вызов функции создает точку геометрии.</span><span class="sxs-lookup"><span data-stu-id="778da-106">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="778da-107"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>Методы имеют все пространственные канонические Entity Framework методы.</span><span class="sxs-lookup"><span data-stu-id="778da-107">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="778da-108">Щелкните интересующий метод, чтобы посмотреть, какие параметры должны быть переданы функции.</span><span class="sxs-lookup"><span data-stu-id="778da-108">Click on a method of interest to see what parameters should be passed to a function.</span></span>
