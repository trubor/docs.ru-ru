---
description: Дополнительные сведения о модуле <keyword> (Visual Basic)
title: Модуль <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 1bd25b00b41f5da4fca535220fe4e1694c81baca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640697"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="5c6c6-103">Module \<keyword> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c6c6-103">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="5c6c6-104">Указывает, что атрибут в начале исходного файла применяется к текущему модулю сборки.</span><span class="sxs-lookup"><span data-stu-id="5c6c6-104">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c6c6-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c6c6-105">Remarks</span></span>  

 <span data-ttu-id="5c6c6-106">Многие атрибуты относятся к отдельному программному элементу, например классу или свойству.</span><span class="sxs-lookup"><span data-stu-id="5c6c6-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="5c6c6-107">Вы применяете такой атрибут, присоединив блок атрибута в угловых скобках ( `< >` ) непосредственно к оператору объявления.</span><span class="sxs-lookup"><span data-stu-id="5c6c6-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="5c6c6-108">Если атрибут относится не только к следующему элементу, но и к текущему модулю сборки, блок атрибута помещается в начало исходного файла и определяется атрибутом с `Module` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="5c6c6-108">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="5c6c6-109">Если он применяется ко всей сборке, используется ключевое слово [Assembly](assembly.md) .</span><span class="sxs-lookup"><span data-stu-id="5c6c6-109">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="5c6c6-110">`Module`Модификатор не совпадает с [оператором module](../statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5c6c6-110">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6c6-111">См. также</span><span class="sxs-lookup"><span data-stu-id="5c6c6-111">See also</span></span>

- [<span data-ttu-id="5c6c6-112">Сборка</span><span class="sxs-lookup"><span data-stu-id="5c6c6-112">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="5c6c6-113">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="5c6c6-113">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="5c6c6-114">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="5c6c6-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
