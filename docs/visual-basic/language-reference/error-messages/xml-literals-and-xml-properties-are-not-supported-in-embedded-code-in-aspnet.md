---
description: 'Дополнительные сведения о: BC31200: XML-литералы и XML-свойства не поддерживаются в внедренном коде в ASP.NET'
title: XML литералы и XML свойства не поддерживаются во встроенном в ASP.NET коде
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 0a5328676ee38a56334b77f665a464daa586ce3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701408"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="6d66b-103">BC31200: XML-литералы и XML-свойства не поддерживаются в внедренном коде в ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6d66b-103">BC31200: XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="6d66b-104">XML-литералы и XML-свойства не поддерживаются во внедренном коде в ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d66b-104">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="6d66b-105">Чтобы использовать функции XML, переместите код в код программной части.</span><span class="sxs-lookup"><span data-stu-id="6d66b-105">To use XML features, move the code to code-behind.</span></span>

 <span data-ttu-id="6d66b-106">XML-литерал или свойство оси XML определяются внутри внедренного кода ( `<%= =>` ) в файле ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d66b-106">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>

 <span data-ttu-id="6d66b-107">**Идентификатор ошибки:** BC31200</span><span class="sxs-lookup"><span data-stu-id="6d66b-107">**Error ID:** BC31200</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6d66b-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6d66b-108">To correct this error</span></span>

- <span data-ttu-id="6d66b-109">Переместите код, включающий XML-литерал или свойство оси XML, в файл кода программной части ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d66b-109">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d66b-110">См. также</span><span class="sxs-lookup"><span data-stu-id="6d66b-110">See also</span></span>

- [<span data-ttu-id="6d66b-111">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="6d66b-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="6d66b-112">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="6d66b-112">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="6d66b-113">XML</span><span class="sxs-lookup"><span data-stu-id="6d66b-113">XML</span></span>](../../programming-guide/language-features/xml/index.md)
