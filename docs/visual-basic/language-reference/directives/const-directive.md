---
description: 'Дополнительные сведения: Директива #Const'
title: '#Директива Const'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 9597666ee1320f5dfda226040f93a84eb60a3deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797280"
---
# <a name="const-directive"></a><span data-ttu-id="83962-103">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="83962-103">#Const Directive</span></span>

<span data-ttu-id="83962-104">Определяет константы условной компилятора для Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="83962-104">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83962-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83962-105">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="83962-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="83962-106">Parts</span></span>  

 `constname`  
 <span data-ttu-id="83962-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="83962-107">Required.</span></span> <span data-ttu-id="83962-108">Имя определяемой константы.</span><span class="sxs-lookup"><span data-stu-id="83962-108">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="83962-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="83962-109">Required.</span></span> <span data-ttu-id="83962-110">Literal, другая условная константа компилятора или любое сочетание, включающее любые или все арифметические или логические операторы, кроме `Is` .</span><span class="sxs-lookup"><span data-stu-id="83962-110">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83962-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="83962-111">Remarks</span></span>  

 <span data-ttu-id="83962-112">Константы условной компиляции всегда являются частными для файла, в котором они отображаются.</span><span class="sxs-lookup"><span data-stu-id="83962-112">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="83962-113">Нельзя создавать открытые константы компилятора с помощью `#Const` директивы. их можно создавать только в пользовательском интерфейсе или с помощью `/define` параметра компилятора.</span><span class="sxs-lookup"><span data-stu-id="83962-113">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="83962-114">В можно использовать только константы условной компиляции и литералы `expression` .</span><span class="sxs-lookup"><span data-stu-id="83962-114">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="83962-115">Использование стандартной константы, определенной с помощью, `Const` приводит к ошибке.</span><span class="sxs-lookup"><span data-stu-id="83962-115">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="83962-116">И наоборот, константы, определенные с помощью `#Const` ключевого слова, можно использовать только для условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="83962-116">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="83962-117">Константы также могут быть неопределенными, в этом случае они имеют значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="83962-117">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83962-118">Пример</span><span class="sxs-lookup"><span data-stu-id="83962-118">Example</span></span>  

 <span data-ttu-id="83962-119">В этом примере используется директива `#Const`.</span><span class="sxs-lookup"><span data-stu-id="83962-119">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="83962-120">См. также</span><span class="sxs-lookup"><span data-stu-id="83962-120">See also</span></span>

- [<span data-ttu-id="83962-121">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83962-121">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="83962-122">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="83962-122">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="83962-123">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="83962-123">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="83962-124">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="83962-124">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="83962-125">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="83962-125">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
