---
description: 'Дополнительные сведения о: BC30007: требуется ссылка на сборку " <assemblyname> ", содержащую базовый класс<classname>'
title: Требуется ссылка на сборку <assemblyname>, содержащую базовый класс <classname>
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: f01795d3e8147015f9f46697b047a8c63099ff32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792054"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="9b3ce-103">BC30007: требуется ссылка на сборку " \<assemblyname> ", содержащую базовый класс " \<classname> "</span><span class="sxs-lookup"><span data-stu-id="9b3ce-103">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="9b3ce-104">Требуется ссылка на сборку " \<assemblyname> ", содержащую базовый класс " \<classname> ".</span><span class="sxs-lookup"><span data-stu-id="9b3ce-104">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="9b3ce-105">Добавьте эту ссылку в проект.</span><span class="sxs-lookup"><span data-stu-id="9b3ce-105">Add one to your project.</span></span>

 <span data-ttu-id="9b3ce-106">Класс определяется в библиотеке динамической компоновки (DLL) или в сборке, на которую в проекте нет прямой ссылки.</span><span class="sxs-lookup"><span data-stu-id="9b3ce-106">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="9b3ce-107">Компилятору Visual Basic требуется ссылка, чтобы избежать неоднозначности в случае, если класс определен в нескольких библиотеках DLL или сборках.</span><span class="sxs-lookup"><span data-stu-id="9b3ce-107">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="9b3ce-108">**Идентификатор ошибки:** BC30007</span><span class="sxs-lookup"><span data-stu-id="9b3ce-108">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9b3ce-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9b3ce-109">To correct this error</span></span>

- <span data-ttu-id="9b3ce-110">Включите в ссылки проекта имя библиотеки DLL или сборки, на которую нет ссылки.</span><span class="sxs-lookup"><span data-stu-id="9b3ce-110">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b3ce-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9b3ce-111">See also</span></span>

- [<span data-ttu-id="9b3ce-112">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="9b3ce-112">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="9b3ce-113">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="9b3ce-113">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
