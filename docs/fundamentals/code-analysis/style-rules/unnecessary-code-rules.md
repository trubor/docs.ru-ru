---
title: Правила, касающиеся ненужного кода
description: Дополнительные сведения правилах, касающихся ненужного кода при анализе кода
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5a60d6b631ff6c73ec1d1087be56a2a023e0fd2c
ms.sourcegitcommit: 040b745ac19e4a5d23df17422ab30e72839f5754
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107809732"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="7802b-103">Правила, касающиеся ненужного кода</span><span class="sxs-lookup"><span data-stu-id="7802b-103">Unnecessary code rules</span></span>

<span data-ttu-id="7802b-104">Правила, касающиеся ненужного кода, определяют различные части базы кода, которые не нужны и могут быть подвергнуты рефакторингу или удалению.</span><span class="sxs-lookup"><span data-stu-id="7802b-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="7802b-105">Наличие ненужного кода указывает на одну из следующих проблем:</span><span class="sxs-lookup"><span data-stu-id="7802b-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="7802b-106">Удобочитаемость: присутствие ненужного кода ухудшает читаемость.</span><span class="sxs-lookup"><span data-stu-id="7802b-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="7802b-107">Например, [IDE0001](ide0001.md) помечает ненужные квалификации type-name.</span><span class="sxs-lookup"><span data-stu-id="7802b-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="7802b-108">Удобство сопровождения: необходимость обслуживать код, который больше не используется после рефакторинга и не нужен.</span><span class="sxs-lookup"><span data-stu-id="7802b-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="7802b-109">Например, [IDE0051](ide0051.md) помечает неиспользуемые закрытые поля, свойства, события и методы.</span><span class="sxs-lookup"><span data-stu-id="7802b-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="7802b-110">Производительность: ненужные вычисления, не имеющие побочных эффектов и ведущие к ненужным издержкам производительности.</span><span class="sxs-lookup"><span data-stu-id="7802b-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="7802b-111">Например, [IDE0059](ide0059.md) помечает неиспользуемые назначения значений, когда выражение для расчета значения не имеет побочных эффектов.</span><span class="sxs-lookup"><span data-stu-id="7802b-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="7802b-112">Функциональность: функциональная проблема в коде, в результате которой требуемый код становится избыточным.</span><span class="sxs-lookup"><span data-stu-id="7802b-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="7802b-113">Например, [IDE0060](ide0060.md) помечает неиспользуемые параметры, когда метод случайно игнорирует входной параметр.</span><span class="sxs-lookup"><span data-stu-id="7802b-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="7802b-114">Правила в этом разделе относятся к следующим правилам, касающимся ненужного кода:</span><span class="sxs-lookup"><span data-stu-id="7802b-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="7802b-115">Упрощение имени (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="7802b-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="7802b-116">Упрощение доступа для членов (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="7802b-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="7802b-117">Удаление ненужных операций приведения (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="7802b-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="7802b-118">Удаление ненужных операций импорта (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="7802b-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="7802b-119">Удаление недоступного кода (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="7802b-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="7802b-120">Удаление неиспользуемых закрытых членов (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="7802b-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="7802b-121">Удаление непрочитанных закрытых членов (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="7802b-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="7802b-122">Удаление ненужного значения выражения (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="7802b-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="7802b-123">Удаление назначения лишних значений (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="7802b-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="7802b-124">Удалите неиспользуемый параметр (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="7802b-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="7802b-125">Удалить ненужное подавление (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="7802b-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="7802b-126">[Удаление ненужного оператора подавления (IDE0080)](ide0080.md) — только C#.</span><span class="sxs-lookup"><span data-stu-id="7802b-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="7802b-127">[Удаление "ByVal" (IDE0081)](ide0081.md) — только Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7802b-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="7802b-128">Удаление ненужного оператора равенства (IDE0100)</span><span class="sxs-lookup"><span data-stu-id="7802b-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="7802b-129">[Удаление ненужной пустой переменной (IDE0110)](ide0110.md) — только C#.</span><span class="sxs-lookup"><span data-stu-id="7802b-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>
- <span data-ttu-id="7802b-130">[Упрощение создания объектов (IDE0140)](ide0140.md) — только Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7802b-130">[Simplify object creation (IDE0140)](ide0140.md) - Visual Basic only.</span></span>

<span data-ttu-id="7802b-131">Некоторые из этих правил имеют параметры для настройки поведения правила:</span><span class="sxs-lookup"><span data-stu-id="7802b-131">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="7802b-132">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="7802b-132">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="7802b-133">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="7802b-133">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="7802b-134">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="7802b-134">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="7802b-135">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="7802b-135">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="7802b-136">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="7802b-136">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="7802b-137">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="7802b-137">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)
- [<span data-ttu-id="7802b-138">visual_basic_style_prefer_simplified_object_creation (IDE0140)</span><span class="sxs-lookup"><span data-stu-id="7802b-138">visual_basic_style_prefer_simplified_object_creation (IDE0140)</span></span>](ide0140.md#visual_basic_style_prefer_simplified_object_creation)

## <a name="see-also"></a><span data-ttu-id="7802b-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7802b-139">See also</span></span>

- [<span data-ttu-id="7802b-140">Правила языка для стиля кода</span><span class="sxs-lookup"><span data-stu-id="7802b-140">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="7802b-141">Справочник по правилам стиля кода</span><span class="sxs-lookup"><span data-stu-id="7802b-141">Code style rules reference</span></span>](index.md)
