---
description: 'Дополнительные сведения о: BC30663: атрибут " <attributename> " не может применяться несколько раз'
title: Атрибут <attributename> не может применяться многократно
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 84b77111a7401eb6f30eb7cd167f4b5689f33e77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797150"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="ec46b-103">BC30663: атрибут " \<attributename> " не может применяться несколько раз</span><span class="sxs-lookup"><span data-stu-id="ec46b-103">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="ec46b-104">Атрибут можно применить только один раз.</span><span class="sxs-lookup"><span data-stu-id="ec46b-104">The attribute can only be applied once.</span></span> <span data-ttu-id="ec46b-105">`AttributeUsage`Атрибут определяет, можно ли применить атрибут более одного раза.</span><span class="sxs-lookup"><span data-stu-id="ec46b-105">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="ec46b-106">**Идентификатор ошибки:** BC30663</span><span class="sxs-lookup"><span data-stu-id="ec46b-106">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec46b-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ec46b-107">To correct this error</span></span>

1. <span data-ttu-id="ec46b-108">Убедитесь, что атрибут применяется только один раз.</span><span class="sxs-lookup"><span data-stu-id="ec46b-108">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="ec46b-109">Если вы используете созданные вами настраиваемые атрибуты, попробуйте изменить их `AttributeUsage` атрибут, чтобы разрешить использование нескольких атрибутов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ec46b-109">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="ec46b-110">См. также</span><span class="sxs-lookup"><span data-stu-id="ec46b-110">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="ec46b-111">Создание настраиваемых атрибутов</span><span class="sxs-lookup"><span data-stu-id="ec46b-111">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="ec46b-112">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="ec46b-112">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
