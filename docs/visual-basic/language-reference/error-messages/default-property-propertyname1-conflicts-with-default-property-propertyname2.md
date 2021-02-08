---
description: 'Дополнительные сведения о: BC40007: свойство по умолчанию " <propertyname1> " конфликтует со свойством по умолчанию " <propertyname2> " в " <classname> " и поэтому должно быть объявлено как "Shadows"'
title: Свойство <propertyname1>, используемое по умолчанию, конфликтует со свойством <propertyname2>, используемым по умолчанию в классе <classname>, и должно быть объявлено с ключевым словом Shadows
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 8ec7e36da18bbf8dda35e1a521d64268d14b7b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796643"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="850e7-103">BC40007: свойство по умолчанию " \<propertyname1> " конфликтует со свойством по умолчанию " \<propertyname2> " в " \<classname> " и поэтому должно быть объявлено как "Shadows"</span><span class="sxs-lookup"><span data-stu-id="850e7-103">BC40007: Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="850e7-104">Свойство объявлено с тем же именем, что и у свойства, определенного в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="850e7-104">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="850e7-105">В этом случае свойство в этом классе должно скрывать свойство базового класса.</span><span class="sxs-lookup"><span data-stu-id="850e7-105">In this situation, the property in this class should shadow the base class property.</span></span>

 <span data-ttu-id="850e7-106">Это сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="850e7-106">This message is a warning.</span></span> <span data-ttu-id="850e7-107">`Shadows` подразумевается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="850e7-107">`Shadows` is assumed by default.</span></span> <span data-ttu-id="850e7-108">Дополнительные сведения о сокрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="850e7-108">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="850e7-109">**Идентификатор ошибки:** BC40007</span><span class="sxs-lookup"><span data-stu-id="850e7-109">**Error ID:** BC40007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="850e7-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="850e7-110">To correct this error</span></span>

- <span data-ttu-id="850e7-111">Добавьте `Shadows` ключевое слово в объявление или измените имя объявляемого свойства.</span><span class="sxs-lookup"><span data-stu-id="850e7-111">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>

## <a name="see-also"></a><span data-ttu-id="850e7-112">См. также</span><span class="sxs-lookup"><span data-stu-id="850e7-112">See also</span></span>

- [<span data-ttu-id="850e7-113">Shadows</span><span class="sxs-lookup"><span data-stu-id="850e7-113">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="850e7-114">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="850e7-114">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
