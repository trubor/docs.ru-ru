---
description: 'Дополнительные сведения о: BC31194: значение типа "тип1" не может быть преобразовано в "тип2"'
title: Невозможно преобразовать значение типа  в
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8cdb5206f0bc09a447ce241921b0efda63792c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674783"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="f5955-103">BC31194: значение типа "тип1" не может быть преобразовано в "тип2"</span><span class="sxs-lookup"><span data-stu-id="f5955-103">BC31194: Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="f5955-104">Значение типа "тип1" не может быть преобразовано в "тип2".</span><span class="sxs-lookup"><span data-stu-id="f5955-104">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="f5955-105">Свойство "value" можно использовать для получения строкового значения первого элемента " \<parentElement> ".</span><span class="sxs-lookup"><span data-stu-id="f5955-105">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>

 <span data-ttu-id="f5955-106">Предпринята попытка неявного приведения XML-литерала к определенному типу.</span><span class="sxs-lookup"><span data-stu-id="f5955-106">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="f5955-107">XML-литерал не может быть неявно приведен к указанному типу.</span><span class="sxs-lookup"><span data-stu-id="f5955-107">The XML literal cannot be implicitly cast to the specified type.</span></span>

 <span data-ttu-id="f5955-108">**Идентификатор ошибки:** BC31194</span><span class="sxs-lookup"><span data-stu-id="f5955-108">**Error ID:** BC31194</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f5955-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f5955-109">To correct this error</span></span>

- <span data-ttu-id="f5955-110">Используйте свойство `Value` XML-литерала для ссылки на его значение как на `String`.</span><span class="sxs-lookup"><span data-stu-id="f5955-110">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="f5955-111">Используйте функцию `CType` , другую функцию преобразования типа или класс <xref:System.Convert> для приведения значения к указанному типу.</span><span class="sxs-lookup"><span data-stu-id="f5955-111">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5955-112">См. также</span><span class="sxs-lookup"><span data-stu-id="f5955-112">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="f5955-113">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="f5955-113">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="f5955-114">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="f5955-114">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="f5955-115">XML</span><span class="sxs-lookup"><span data-stu-id="f5955-115">XML</span></span>](../../programming-guide/language-features/xml/index.md)
