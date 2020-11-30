---
title: Практическое руководство. Совместное использование сборки с другими приложениями
description: Узнайте о том, как можно использовать сборку совместно с другими приложениями в .NET. Сборки могут быть частными (по умолчанию) или общими. Чтобы предоставить общий доступ к сборке, поместите ее в глобальный кэш сборок.
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242543"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="6f837-105">Практическое руководство. Совместное использование сборки с другими приложениями</span><span class="sxs-lookup"><span data-stu-id="6f837-105">How to: Share an assembly with other applications</span></span>

<span data-ttu-id="6f837-106">Сборки могут быть закрытыми или общими. По умолчанию большинство простых программ состоят из закрытой сборки, так как она не предназначена для использования другими приложениями.</span><span class="sxs-lookup"><span data-stu-id="6f837-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="6f837-107">Для совместного использования сборки с другими приложениями ее нужно поместить в [глобальный кэш сборок (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="6f837-108">Предоставление общего доступа к сборке:</span><span class="sxs-lookup"><span data-stu-id="6f837-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="6f837-109">Создайте сборку.</span><span class="sxs-lookup"><span data-stu-id="6f837-109">Create your assembly.</span></span> <span data-ttu-id="6f837-110">Дополнительные сведения см. в разделе [Создание сборок](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="6f837-111">Назначьте сборке строгое имя.</span><span class="sxs-lookup"><span data-stu-id="6f837-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="6f837-112">Дополнительные сведения см. в разделе [Практическое руководство. Подписание сборки со строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="6f837-113">Назначьте сведения о версии для сборки.</span><span class="sxs-lookup"><span data-stu-id="6f837-113">Assign version information to your assembly.</span></span> <span data-ttu-id="6f837-114">Дополнительные сведения см. в разделе [Управление версиями сборок](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="6f837-115">Добавьте сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="6f837-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="6f837-116">Дополнительные сведения см. в разделе [Практическое руководство. Установка сборки в глобальный кэш сборок](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="6f837-117">Получите доступ к типам, содержащимся в сборке, из других приложений.</span><span class="sxs-lookup"><span data-stu-id="6f837-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="6f837-118">Дополнительные сведения см. в разделе [Практическое руководство. Ссылка на сборку со строгим именем](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f837-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6f837-119">See also</span></span>

- [<span data-ttu-id="6f837-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="6f837-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="6f837-121">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f837-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="6f837-122">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="6f837-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
