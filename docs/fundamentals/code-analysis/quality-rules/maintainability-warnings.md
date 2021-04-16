---
title: Правила удобства поддержки (анализ кода)
description: Узнайте больше о правилах удобства поддержки для анализа кода.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592407"
---
# <a name="maintainability-rules"></a><span data-ttu-id="39a49-103">Правила удобства поддержки</span><span class="sxs-lookup"><span data-stu-id="39a49-103">Maintainability rules</span></span>

<span data-ttu-id="39a49-104">Правила удобства поддержки распространяются на обслуживание библиотек и приложений.</span><span class="sxs-lookup"><span data-stu-id="39a49-104">Maintainability rules support library and application maintenance.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="39a49-105">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="39a49-105">In this section</span></span>

| <span data-ttu-id="39a49-106">Правило</span><span class="sxs-lookup"><span data-stu-id="39a49-106">Rule</span></span> | <span data-ttu-id="39a49-107">Описание</span><span class="sxs-lookup"><span data-stu-id="39a49-107">Description</span></span> |
|-----------|-----------------------------------|
| [<span data-ttu-id="39a49-108">CA1501. Избегайте излишнего наследования</span><span class="sxs-lookup"><span data-stu-id="39a49-108">CA1501: Avoid excessive inheritance</span></span>](ca1501.md) | <span data-ttu-id="39a49-109">Тип расположен глубже четырех уровней в иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="39a49-109">A type is more than four levels deep in its inheritance hierarchy.</span></span> <span data-ttu-id="39a49-110">Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать.</span><span class="sxs-lookup"><span data-stu-id="39a49-110">Deeply nested type hierarchies can be difficult to follow, understand, and maintain.</span></span> |
| [<span data-ttu-id="39a49-111">CA1502. Избегайте чрезмерной сложности</span><span class="sxs-lookup"><span data-stu-id="39a49-111">CA1502: Avoid excessive complexity</span></span>](ca1502.md) | <span data-ttu-id="39a49-112">Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей.</span><span class="sxs-lookup"><span data-stu-id="39a49-112">This rule measures the number of linearly independent paths through the method, which is determined by the number and complexity of conditional branches.</span></span> |
| [<span data-ttu-id="39a49-113">CA1505. Избегайте кода, неудобного для поддержки</span><span class="sxs-lookup"><span data-stu-id="39a49-113">CA1505: Avoid unmaintainable code</span></span>](ca1505.md) | <span data-ttu-id="39a49-114">Тип или метод имеет низкий индекс обслуживаемости.</span><span class="sxs-lookup"><span data-stu-id="39a49-114">A type or method has a low maintainability index value.</span></span> <span data-ttu-id="39a49-115">Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать.</span><span class="sxs-lookup"><span data-stu-id="39a49-115">A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate for redesign.</span></span> |
| [<span data-ttu-id="39a49-116">CA1506. Избегайте чрезмерной взаимозависимости классов</span><span class="sxs-lookup"><span data-stu-id="39a49-116">CA1506: Avoid excessive class coupling</span></span>](ca1506.md) | <span data-ttu-id="39a49-117">Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.</span><span class="sxs-lookup"><span data-stu-id="39a49-117">This rule measures class coupling by counting the number of unique type references that a type or method contains.</span></span> |
| [<span data-ttu-id="39a49-118">CA1507: Используйте nameof вместо строки</span><span class="sxs-lookup"><span data-stu-id="39a49-118">CA1507: Use nameof in place of string</span></span>](ca1507.md) | <span data-ttu-id="39a49-119">Строковый литерал используется в качестве аргумента, где можно использовать выражение `nameof`.</span><span class="sxs-lookup"><span data-stu-id="39a49-119">A string literal is used as an argument where a `nameof` expression could be used.</span></span> |
| [<span data-ttu-id="39a49-120">CA1508: Избегайте появления неиспользуемого условного кода</span><span class="sxs-lookup"><span data-stu-id="39a49-120">CA1508: Avoid dead conditional code</span></span>](ca1508.md) | <span data-ttu-id="39a49-121">Метод имеет код условия, который всегда вычисляется как `true` или `false` в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="39a49-121">A method has conditional code that always evaluates to `true` or `false` at runtime.</span></span> <span data-ttu-id="39a49-122">Это приводит к неиспользуемому коду в ветви `false` условия.</span><span class="sxs-lookup"><span data-stu-id="39a49-122">This leads to dead code in the `false` branch of the condition.</span></span> |
| [<span data-ttu-id="39a49-123">CA1509: недопустимая запись в файле конфигурации метрик кода</span><span class="sxs-lookup"><span data-stu-id="39a49-123">CA1509: Invalid entry in code metrics configuration file</span></span>](ca1509.md) | <span data-ttu-id="39a49-124">Правила метрик кода, такие как [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) и [CA1506](ca1506.md), предоставили файл конфигурации с именем `CodeMetricsConfig.txt`, который имеет недопустимую запись.</span><span class="sxs-lookup"><span data-stu-id="39a49-124">Code metrics rules, such as [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) and [CA1506](ca1506.md), supplied a configuration file named `CodeMetricsConfig.txt` that has an invalid entry.</span></span> |

## <a name="see-also"></a><span data-ttu-id="39a49-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="39a49-125">See also</span></span>

- [<span data-ttu-id="39a49-126">Оценка сложности и удобства сопровождения управляемого кода</span><span class="sxs-lookup"><span data-stu-id="39a49-126">Measure Complexity and Maintainability of Managed Code</span></span>](/visualstudio/code-quality/code-metrics-values)
