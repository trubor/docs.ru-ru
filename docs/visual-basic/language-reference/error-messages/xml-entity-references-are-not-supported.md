---
description: 'Дополнительные сведения о: BC31180: ссылки на сущности XML не поддерживаются'
title: Ссылки на XML-сущности не поддерживаются
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: c45202fbd97d2343caf6bf4cdccf9368d0a7a295
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701421"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a><span data-ttu-id="95185-103">BC31180: ссылки на сущности XML не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="95185-103">BC31180: XML entity references are not supported</span></span>

<span data-ttu-id="95185-104">Ссылка на сущность (например, `©` ), не определенная в спецификации xml 1,0, включается в качестве значения XML-литерала.</span><span class="sxs-lookup"><span data-stu-id="95185-104">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="95185-105">`&` `"` `<` `>` `'` В XML-литералах поддерживаются только ссылки на XML-сущности,,, и.</span><span class="sxs-lookup"><span data-stu-id="95185-105">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>

 <span data-ttu-id="95185-106">**Идентификатор ошибки:** BC31180</span><span class="sxs-lookup"><span data-stu-id="95185-106">**Error ID:** BC31180</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="95185-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="95185-107">To correct this error</span></span>

- <span data-ttu-id="95185-108">Удалите неподдерживаемую ссылку на сущность.</span><span class="sxs-lookup"><span data-stu-id="95185-108">Remove the unsupported entity reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="95185-109">См. также</span><span class="sxs-lookup"><span data-stu-id="95185-109">See also</span></span>

- [<span data-ttu-id="95185-110">XML-литералы и спецификация XML 1.0</span><span class="sxs-lookup"><span data-stu-id="95185-110">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="95185-111">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="95185-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="95185-112">XML</span><span class="sxs-lookup"><span data-stu-id="95185-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
