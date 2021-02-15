---
description: Дополнительные сведения о ключевых словах в виде имен элементов в коде (Visual Basic)
title: Ключевые слова как имена элементов в коде
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4782c0f3ea065e3e140d449575c187cf2254cd08
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433217"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="eeb13-103">Ключевые слова как имена элементов в коде (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeb13-103">Keywords as Element Names in Code (Visual Basic)</span></span>

<span data-ttu-id="eeb13-104">Любой элемент программы (например, переменная, класс или член) может иметь то же имя, что и ключевое слово Restricted.</span><span class="sxs-lookup"><span data-stu-id="eeb13-104">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="eeb13-105">Например, можно создать переменную с именем `Loop` .</span><span class="sxs-lookup"><span data-stu-id="eeb13-105">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="eeb13-106">Однако для ссылки на вашу версию, которая имеет то же имя, что и ключевое слово Restricted, `Loop` необходимо либо указать перед ней полную уточняющую строку, либо заключить ее в квадратные скобки ( `[ ]` ), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="eeb13-106">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="eeb13-107">Если вы не выполняете ни одно из этих действий, Visual Basic предполагает использование встроенного `Loop` ключевого слова и выдает ошибку, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="eeb13-107">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="eeb13-108">При обращении к формам и элементам управления можно использовать квадратные скобки, а также при объявлении переменной или при определении процедуры с тем же именем, что и ключевое слово Restricted.</span><span class="sxs-lookup"><span data-stu-id="eeb13-108">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="eeb13-109">Можно легко забыть определить имена или включить в них квадратные скобки, что приводит к ошибкам в коде и затрудняет чтение.</span><span class="sxs-lookup"><span data-stu-id="eeb13-109">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="eeb13-110">По этой причине не рекомендуется использовать в качестве имен программных элементов ограниченные ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="eeb13-110">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="eeb13-111">Однако если в будущей версии Visual Basic определено новое ключевое слово, которое вступает в противоречие с существующей формой или именем элемента управления, можно использовать этот метод при обновлении кода для работы с новой версией.</span><span class="sxs-lookup"><span data-stu-id="eeb13-111">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eeb13-112">Программа также может включать имена элементов, предоставляемых другими ссылочными сборками.</span><span class="sxs-lookup"><span data-stu-id="eeb13-112">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="eeb13-113">Если эти имена конфликтуют с ограниченными ключевыми словами, то при заключении в квадратные скобки они приводят к тому, что Visual Basic интерпретирует их как определенные элементы.</span><span class="sxs-lookup"><span data-stu-id="eeb13-113">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeb13-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="eeb13-114">See also</span></span>

- [<span data-ttu-id="eeb13-115">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eeb13-115">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="eeb13-116">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="eeb13-116">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="eeb13-117">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="eeb13-117">Keywords</span></span>](../../language-reference/keywords/index.md)
