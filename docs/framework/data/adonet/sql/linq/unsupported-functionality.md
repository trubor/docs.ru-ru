---
description: 'Дополнительные сведения: неподдерживаемые функции'
title: Неподдерживаемые функциональные возможности
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5c44dd4aad2d2ee4ec5e00ce42f4de9400cea478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680893"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="66ea6-103">Неподдерживаемые функциональные возможности</span><span class="sxs-lookup"><span data-stu-id="66ea6-103">Unsupported Functionality</span></span>

<span data-ttu-id="66ea6-104">В LINQ to SQL следующие функции SQL недоступны путем преобразования существующих конструкций среды CLR и .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66ea6-104">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="66ea6-105">Хотя функция `LIKE` не поддерживается прямым преобразованием, аналогичная функция существует в классе <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="66ea6-105">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="66ea6-106">Для получения дополнительной информации см. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66ea6-106">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="66ea6-107">В LINQ to SQL реализована ограниченная поддержка функции `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="66ea6-107">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="66ea6-108">Аналогичная функция существует в классе <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="66ea6-108">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="66ea6-109">В LINQ to SQL реализована ограниченная поддержка функции `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="66ea6-109">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="66ea6-110">Дополнительные сведения см. в разделе [методы System. Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="66ea6-110">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ea6-111">См. также</span><span class="sxs-lookup"><span data-stu-id="66ea6-111">See also</span></span>

- [<span data-ttu-id="66ea6-112">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="66ea6-112">Data Types and Functions</span></span>](data-types-and-functions.md)
