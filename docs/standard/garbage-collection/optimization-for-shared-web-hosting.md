---
title: Оптимизация совместного размещения веб-сайтов
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: abab4ac451a70fbc81ac6d7c9da6f8d0123287a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669033"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="be4af-102">Оптимизация совместного размещения веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="be4af-102">Optimization for Shared Web Hosting</span></span>

<span data-ttu-id="be4af-103">Если вы являетесь администратором сервера, на котором совместно размещены несколько небольших веб-сайтов, производительность и емкость такого сайта можно увеличить, добавив следующий параметр `gcTrimCommitOnLowMemory` в узел `runtime` файла Aspnet.config, расположенного в каталоге .NET.</span><span class="sxs-lookup"><span data-stu-id="be4af-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="be4af-104">Этот параметр рекомендуется применять только в сценариях совместного размещения веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="be4af-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="be4af-105">Так как сборщик мусора сохраняет память для будущих распределений, он может выделять для них больше памяти, чем строго необходимо.</span><span class="sxs-lookup"><span data-stu-id="be4af-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="be4af-106">Вы можете уменьшить этот объем, чтобы снизить нагрузку на системную память.</span><span class="sxs-lookup"><span data-stu-id="be4af-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="be4af-107">Уменьшение выделяемого объема повышает производительность и емкость, позволяя разместить большее количество узлов.</span><span class="sxs-lookup"><span data-stu-id="be4af-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="be4af-108">Если включен параметр `gcTrimCommitOnLowMemory`, сборщик мусора оценивает загрузку системной памяти и переходит в режим обрезки, если нагрузка достигает 90 %.</span><span class="sxs-lookup"><span data-stu-id="be4af-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="be4af-109">Режим обрезки сохраняется, пока загрузка не опустится ниже 85 %.</span><span class="sxs-lookup"><span data-stu-id="be4af-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="be4af-110">В некоторых условиях сборщик мусора полагает, что параметр `gcTrimCommitOnLowMemory` не может помочь работающему приложению, и тогда игнорирует его.</span><span class="sxs-lookup"><span data-stu-id="be4af-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be4af-111">Пример</span><span class="sxs-lookup"><span data-stu-id="be4af-111">Example</span></span>  

 <span data-ttu-id="be4af-112">В следующем фрагменте XML показано, как включить параметр `gcTrimCommitOnLowMemory`.</span><span class="sxs-lookup"><span data-stu-id="be4af-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="be4af-113">Многоточие обозначает все другие параметры, которые находятся в узле `runtime`.</span><span class="sxs-lookup"><span data-stu-id="be4af-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be4af-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="be4af-114">See also</span></span>

- [<span data-ttu-id="be4af-115">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="be4af-115">Garbage Collection</span></span>](index.md)
