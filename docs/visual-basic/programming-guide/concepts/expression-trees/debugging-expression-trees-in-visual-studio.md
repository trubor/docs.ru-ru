---
description: Дополнительные сведения см. в статье Отладка деревьев выражений в Visual Studio (Visual Basic)
title: Отладка деревьев выражений в Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 0221533a79dbc76be479380bd9b6e6df4156e288
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100459088"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="0311f-103">Отладка деревьев выражений в Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0311f-103">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="0311f-104">При отладке приложений можно анализировать структуру и содержимое деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="0311f-104">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="0311f-105">Чтобы получить краткий обзор структуры дерева выражения, вы можете использовать свойство `DebugView`, которое представляет деревья выражений, [используя специальный синтаксис](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="0311f-105">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="0311f-106">(Обратите внимание, что `DebugView` доступен только в режиме отладки.)</span><span class="sxs-lookup"><span data-stu-id="0311f-106">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Снимок экрана DebugView дерева выражения.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="0311f-108">Так как `DebugView` представляет собой строку, можно использовать [встроенный визуализатор текста](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) для его просмотра по нескольким строкам, выбрав **визуализатор текста** из меню со значком лупы рядом с меткой `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="0311f-108">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Снимок экрана: визуализатор текста, примененный к результатам DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="0311f-110">Или вы можете установить и использовать [пользовательский визуализатор](/visualstudio/debugger/create-custom-visualizers-of-data) для деревьев выражений, например:</span><span class="sxs-lookup"><span data-stu-id="0311f-110">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="0311f-111">[Выражения для чтения](https://github.com/agileobjects/ReadableExpressions) ([лицензия MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), доступная в [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) отображают дерево выражения в виде кода C# с темой и различными вариантами отрисовки:</span><span class="sxs-lookup"><span data-stu-id="0311f-111">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Снимок экрана: визуализатор доступных для чтения выражений](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="0311f-113">[Визуализатор дерева выражений](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([Лицензия MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) предоставляет древовидное представление дерева выражения и его отдельных узлов. и могут визуализировать дерево выражения с помощью синтаксиса Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="0311f-113">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Снимок экрана: визуализатор дерева выражений](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="0311f-115">Открытие визуализатора дерева выражения</span><span class="sxs-lookup"><span data-stu-id="0311f-115">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="0311f-116">Щелкните значок лупы рядом с деревом выражения в окне **Подсказки по данным**, **Контрольные значения**, **Видимые** или **Локальные**.</span><span class="sxs-lookup"><span data-stu-id="0311f-116">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="0311f-117">Отображается список доступных визуализаторов:</span><span class="sxs-lookup"><span data-stu-id="0311f-117">A list of available visualizers is displayed.:</span></span>

    ![Снимок экрана пользователя, открывающего визуализаторы из Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="0311f-119">Щелкните визуализатор, который необходимо использовать.</span><span class="sxs-lookup"><span data-stu-id="0311f-119">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0311f-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0311f-120">See also</span></span>

- <span data-ttu-id="0311f-121">[Expression Trees (Visual Basic)](index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="0311f-121">[Expression Trees (Visual Basic)](index.md)</span></span>
- [<span data-ttu-id="0311f-122">Отладка в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0311f-122">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="0311f-123">Создание настраиваемых визуализаторов</span><span class="sxs-lookup"><span data-stu-id="0311f-123">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="0311f-124">Синтаксис `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0311f-124">`DebugView` syntax</span></span>](debugview-syntax.md)
