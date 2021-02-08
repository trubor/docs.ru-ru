---
description: 'Дополнительные сведения о: BC30188: ожидается объявление'
title: Ожидается объявление
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: b86c182fb9dc8ab7d624833136f0e87b072aed92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796669"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="17a55-103">BC30188: ожидается объявление</span><span class="sxs-lookup"><span data-stu-id="17a55-103">BC30188: Declaration expected</span></span>

<span data-ttu-id="17a55-104">Недекларативный оператор, такой как оператор присваивания или цикла, происходит вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="17a55-104">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="17a55-105">За пределами процедур разрешены только объявления.</span><span class="sxs-lookup"><span data-stu-id="17a55-105">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="17a55-106">Кроме того, программный элемент объявляется без ключевого слова объявления, такого как `Dim` или `Const` .</span><span class="sxs-lookup"><span data-stu-id="17a55-106">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="17a55-107">**Идентификатор ошибки:** BC30188</span><span class="sxs-lookup"><span data-stu-id="17a55-107">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="17a55-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="17a55-108">To correct this error</span></span>

- <span data-ttu-id="17a55-109">Переместите недекларативный оператор в тело процедуры.</span><span class="sxs-lookup"><span data-stu-id="17a55-109">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="17a55-110">Начните объявление с помощью соответствующего ключевого слова объявления.</span><span class="sxs-lookup"><span data-stu-id="17a55-110">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="17a55-111">Убедитесь, что ключевое слово объявления написано неправильно.</span><span class="sxs-lookup"><span data-stu-id="17a55-111">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="17a55-112">См. также</span><span class="sxs-lookup"><span data-stu-id="17a55-112">See also</span></span>

- [<span data-ttu-id="17a55-113">Процедуры</span><span class="sxs-lookup"><span data-stu-id="17a55-113">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="17a55-114">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="17a55-114">Dim Statement</span></span>](../statements/dim-statement.md)
