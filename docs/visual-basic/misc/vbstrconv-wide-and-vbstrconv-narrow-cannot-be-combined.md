---
description: 'Дополнительные сведения: VbStrConv. Wide и VbStrConv. Narrow не могут быть объединены'
title: VbStrConv.Wide и VbStrConv.Narrow не могут использоваться вместе
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 422c699bd06709368ea4f8948c4b2824a643e342
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475673"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a><span data-ttu-id="1fbd5-103">VbStrConv.Wide и VbStrConv.Narrow не могут использоваться вместе</span><span class="sxs-lookup"><span data-stu-id="1fbd5-103">VbStrConv.Wide and VbStrConv.Narrow cannot be combined</span></span>

<span data-ttu-id="1fbd5-104">Приложение пытается объединить взаимоисключающие элементы `VbStrConv` и `Wide` перечисления `Narrow`.</span><span class="sxs-lookup"><span data-stu-id="1fbd5-104">Your application is trying to combine the `VbStrConv` enumeration members `Wide` and `Narrow`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1fbd5-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="1fbd5-105">To correct this error</span></span>  
  
1. <span data-ttu-id="1fbd5-106">Удалите `VbStrConv.Wide` или `VbStrConv.Narrow`.</span><span class="sxs-lookup"><span data-stu-id="1fbd5-106">Remove either `VbStrConv.Wide` or `VbStrConv.Narrow`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fbd5-107">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1fbd5-107">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="1fbd5-108">Разработка глобализованных и локализованных приложений</span><span class="sxs-lookup"><span data-stu-id="1fbd5-108">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
