---
description: Дополнительные сведения о том, как перемещать данные в переменную или из нее (Visual Basic).
title: Практическое руководство. Запись данных в переменную и их извлечение из переменной
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: e75be83f82a3e1418099375eb52a2d2cc4fdbd18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481822"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="b2591-103">Практическое руководство. Запись данных в переменную и их извлечение из переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2591-103">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="b2591-104">Значение сохраняется в переменной путем размещения имени переменной в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="b2591-104">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="b2591-105">Помещение данных в переменную</span><span class="sxs-lookup"><span data-stu-id="b2591-105">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="b2591-106">Сохранение значения в переменной</span><span class="sxs-lookup"><span data-stu-id="b2591-106">To store a value in a variable</span></span>

- <span data-ttu-id="b2591-107">Используйте имя переменной в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="b2591-107">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="b2591-108">В следующем примере задается значение переменной `alpha` .</span><span class="sxs-lookup"><span data-stu-id="b2591-108">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="b2591-109">Значение, созданное в правой части оператора присваивания, хранится в переменной.</span><span class="sxs-lookup"><span data-stu-id="b2591-109">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="b2591-110">Получение данных из переменной</span><span class="sxs-lookup"><span data-stu-id="b2591-110">Getting Data from a Variable</span></span>

<span data-ttu-id="b2591-111">Значение переменной извлекается путем включения имени переменной в выражение.</span><span class="sxs-lookup"><span data-stu-id="b2591-111">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="b2591-112">Получение значения из переменной</span><span class="sxs-lookup"><span data-stu-id="b2591-112">To retrieve a value from a variable</span></span>

- <span data-ttu-id="b2591-113">Используйте имя переменной в выражении.</span><span class="sxs-lookup"><span data-stu-id="b2591-113">Use the variable name in an expression.</span></span> <span data-ttu-id="b2591-114">Можно использовать переменную в любом месте, где можно использовать константу или литерал, за исключением выражения, определяющего значение константы.</span><span class="sxs-lookup"><span data-stu-id="b2591-114">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="b2591-115">\-или-</span><span class="sxs-lookup"><span data-stu-id="b2591-115">\-or-</span></span>

- <span data-ttu-id="b2591-116">Используйте имя переменной после знака равенства ( `=` ) в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="b2591-116">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="b2591-117">В следующем примере считывается значение переменной `startValue` , а затем используется значение переменной `counter` в выражении.</span><span class="sxs-lookup"><span data-stu-id="b2591-117">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="b2591-118">Значение переменной участвует в выражении точно так же, как константа, а затем хранится в переменной или свойстве в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="b2591-118">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2591-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b2591-119">See also</span></span>

- [<span data-ttu-id="b2591-120">Переменные</span><span class="sxs-lookup"><span data-stu-id="b2591-120">Variables</span></span>](index.md)
- [<span data-ttu-id="b2591-121">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="b2591-121">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="b2591-122">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="b2591-122">Object Variables</span></span>](object-variables.md)
