---
description: 'Дополнительные сведения о: BC30251: тип " <typename> " не имеет конструкторов'
title: В типе <typename> отсутствуют конструкторы
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 32ae854e9f1b037a17d9c378ce7ee4a3f9b43ad2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641178"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="e328b-103">BC30251: тип " \<typename> " не имеет конструкторов</span><span class="sxs-lookup"><span data-stu-id="e328b-103">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="e328b-104">Тип не поддерживает вызов в `Sub New()`.</span><span class="sxs-lookup"><span data-stu-id="e328b-104">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="e328b-105">Одной из возможных причин является повреждение компилятора или двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="e328b-105">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="e328b-106">**Идентификатор ошибки:** BC30251</span><span class="sxs-lookup"><span data-stu-id="e328b-106">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e328b-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e328b-107">To correct this error</span></span>

1. <span data-ttu-id="e328b-108">Если тип находится в другом проекте или в заданном ссылкой файле, переустановите этот проект или файл.</span><span class="sxs-lookup"><span data-stu-id="e328b-108">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="e328b-109">Если тип находится в том же самом проекте, перекомпилируйте сборку, содержащую тип.</span><span class="sxs-lookup"><span data-stu-id="e328b-109">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="e328b-110">Если ошибка повторяется, переустановите компилятор Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e328b-110">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="e328b-111">Если ошибка не устранена, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e328b-111">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="e328b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e328b-112">See also</span></span>

- [<span data-ttu-id="e328b-113">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="e328b-113">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="e328b-114">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="e328b-114">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
