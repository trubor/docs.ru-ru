---
title: Правила, касающиеся ненужного кода
description: Дополнительные сведения о ненужных правилах кода для анализа кода
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "96593858"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="5e45e-103">Правила, касающиеся ненужного кода</span><span class="sxs-lookup"><span data-stu-id="5e45e-103">Unnecessary code rules</span></span>

<span data-ttu-id="5e45e-104">Ненужные правила кода определяют различные части базы кода, которые не нужны и могут быть подвергнуты рефакторингу или удалению.</span><span class="sxs-lookup"><span data-stu-id="5e45e-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="5e45e-105">Наличие ненужного кода указывает на одну из следующих проблем:</span><span class="sxs-lookup"><span data-stu-id="5e45e-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="5e45e-106">Удобочитаемость: код, который необязательно ухудшает читаемость.</span><span class="sxs-lookup"><span data-stu-id="5e45e-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="5e45e-107">Например, [IDE0001](ide0001.md) помечает ненужные квалификации типа Name.</span><span class="sxs-lookup"><span data-stu-id="5e45e-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="5e45e-108">Удобство сопровождения: код, который больше не используется после рефакторинга и необязательно обслуживается.</span><span class="sxs-lookup"><span data-stu-id="5e45e-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="5e45e-109">Например, [IDE0051](ide0051.md) помечает неиспользуемые закрытые поля, свойства, события и методы.</span><span class="sxs-lookup"><span data-stu-id="5e45e-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="5e45e-110">Производительность: ненужные вычисления, не имеющие побочных эффектов и ведущие к ненужным издержкам на производительность.</span><span class="sxs-lookup"><span data-stu-id="5e45e-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="5e45e-111">Например, [IDE0059](ide0059.md) помечает неиспользуемые назначения значений, когда выражение для расчета значения не имеет побочных эффектов.</span><span class="sxs-lookup"><span data-stu-id="5e45e-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="5e45e-112">Функциональность: функциональная ошибка в коде, ведущая к требуемому коду, который подготавливается к просмотру избыточным.</span><span class="sxs-lookup"><span data-stu-id="5e45e-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="5e45e-113">Например, [IDE0060](ide0060.md) помечает неиспользуемые параметры, когда метод случайно игнорирует входной параметр.</span><span class="sxs-lookup"><span data-stu-id="5e45e-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="5e45e-114">Правила в этом разделе касаются следующих ненужных правил кода:</span><span class="sxs-lookup"><span data-stu-id="5e45e-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="5e45e-115">Упростите имя (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="5e45e-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="5e45e-116">Упрощение доступа к членам (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="5e45e-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="5e45e-117">Удалить ненужное приведение (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="5e45e-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="5e45e-118">Удалить ненужный импорт (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="5e45e-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="5e45e-119">Удаление недостижимого кода (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="5e45e-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="5e45e-120">Удалить неиспользуемый частный член (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="5e45e-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="5e45e-121">Удалить непрочтенный частный член (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="5e45e-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="5e45e-122">Удалить неиспользуемое значение выражения (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="5e45e-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="5e45e-123">Удалить ненужное назначение значения (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="5e45e-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="5e45e-124">Удалить неиспользуемый параметр (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="5e45e-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="5e45e-125">Удалить ненужное подавление (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="5e45e-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="5e45e-126">[Удалить ненужный оператор подавления (IDE0080)](ide0080.md) — только C#.</span><span class="sxs-lookup"><span data-stu-id="5e45e-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="5e45e-127">[Удалить "ByVal" (IDE0081)](ide0081.md) — только Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5e45e-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="5e45e-128">Удалить ненужный оператор равенства (IDE0100)</span><span class="sxs-lookup"><span data-stu-id="5e45e-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="5e45e-129">[Удалите ненужный отказ (IDE0110)](ide0110.md) — только C#.</span><span class="sxs-lookup"><span data-stu-id="5e45e-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="5e45e-130">Некоторые из этих правил имеют параметры для настройки поведения правила.</span><span class="sxs-lookup"><span data-stu-id="5e45e-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="5e45e-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="5e45e-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="5e45e-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="5e45e-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="5e45e-133">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="5e45e-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="5e45e-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="5e45e-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="5e45e-135">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="5e45e-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="5e45e-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="5e45e-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="5e45e-137">См. также</span><span class="sxs-lookup"><span data-stu-id="5e45e-137">See also</span></span>

- [<span data-ttu-id="5e45e-138">Правила языка для стиля кода</span><span class="sxs-lookup"><span data-stu-id="5e45e-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="5e45e-139">Справочник по правилам стиля кода</span><span class="sxs-lookup"><span data-stu-id="5e45e-139">Code style rules reference</span></span>](index.md)
