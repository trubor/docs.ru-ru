---
title: Устранение рисков. Макет WPF
description: Узнайте, как устранить проблемы, возникающие в результате изменений в макете элементов управления WPF, таких как размещение объекта, перемещаемого на один пиксель.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244084"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="e0f0e-103">Устранение рисков. Макет WPF</span><span class="sxs-lookup"><span data-stu-id="e0f0e-103">Mitigation: WPF Layout</span></span>

<span data-ttu-id="e0f0e-104">Макет элементов управления WPF может немного изменяться.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e0f0e-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="e0f0e-105">Impact</span></span>  

 <span data-ttu-id="e0f0e-106">В результате этого изменения:</span><span class="sxs-lookup"><span data-stu-id="e0f0e-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="e0f0e-107">ширина или высота элементов может увеличиться или уменьшиться максимум на один пиксель;</span><span class="sxs-lookup"><span data-stu-id="e0f0e-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="e0f0e-108">расположение объекта может измениться максимум на один пиксель;</span><span class="sxs-lookup"><span data-stu-id="e0f0e-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="e0f0e-109">выровненные по центру элементы могут сместиться по вертикали или горизонтали максимум на один пиксель.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="e0f0e-110">По умолчанию новый макет включен только для приложений, предназначенных для .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e0f0e-111">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="e0f0e-111">Mitigation</span></span>  

 <span data-ttu-id="e0f0e-112">Поскольку это изменение, как правило, приводит к устранению обрезки правых или нижних элементов управления WPF при высоком разрешении, для приложений, предназначенных для более ранних версий .NET Framework, но выполняющихся в .NET Framework 4.6, можно выбрать это новое поведение, добавив следующую строку в раздел `<runtime>` файла app.config.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="e0f0e-113">Для приложений, предназначенных для .NET Framework 4.6, для которых требуется задать отрисовку элементов управления WPF с помощью прежнего алгоритма макета, можно добавить следующую строку в раздел `<runtime>` файла app.config.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0f0e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="e0f0e-114">See also</span></span>

- [<span data-ttu-id="e0f0e-115">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="e0f0e-115">Application compatibility</span></span>](application-compatibility.md)
