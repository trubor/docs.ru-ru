---
description: 'Дополнительные сведения: Производные математические функции (Visual Basic)'
title: Производные математические функции
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: daaed1312f08cecc0c68af0e36d574424fc526a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730776"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="ebfa9-103">Производные математические функции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-103">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="ebfa9-104">В следующей таблице показаны невстроенные математические функции, которые могут быть производными от встроенных математических функций <xref:System.Math?displayProperty=nameWithType> объекта.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-104">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="ebfa9-105">Доступ к встроенным математическим функциям можно получить, добавив `Imports System.Math` в файл или проект.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-105">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="ebfa9-106">Компонент</span><span class="sxs-lookup"><span data-stu-id="ebfa9-106">Function</span></span>|<span data-ttu-id="ebfa9-107">Производные эквиваленты</span><span class="sxs-lookup"><span data-stu-id="ebfa9-107">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="ebfa9-108">Секанс (с (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-108">Secant (Sec(x))</span></span>|<span data-ttu-id="ebfa9-109">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-109">1 / Cos(x)</span></span>|  
|<span data-ttu-id="ebfa9-110">Косеканс (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-110">Cosecant (Csc(x))</span></span>|<span data-ttu-id="ebfa9-111">1/Sin (x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-111">1 / Sin(x)</span></span>|  
|<span data-ttu-id="ebfa9-112">Котангенс (Ктан (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-112">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="ebfa9-113">1/Tan (x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-113">1 / Tan(x)</span></span>|  
|<span data-ttu-id="ebfa9-114">Обратный Синус (ASIN (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-114">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="ebfa9-115">ATAN (x/Sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-115">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="ebfa9-116">Обратный косинус (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-116">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="ebfa9-117">ATAN (-x/Sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-117">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="ebfa9-118">Обратный секанс (АСЕК (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-118">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="ebfa9-119">2 \* ATAN (1) — ATAN (Sign (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-119">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ebfa9-120">Обратный косеканс (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-120">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="ebfa9-121">ATAN (Sign (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-121">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ebfa9-122">Обратная котангенс (Акот (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-122">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="ebfa9-123">2 \* ATAN (1) — ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-123">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="ebfa9-124">Гиперболический синус (SINH (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-124">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="ebfa9-125">(Exp (x) – EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-125">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ebfa9-126">Гиперболический косинус (COSH (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-126">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="ebfa9-127">(Exp (x) + EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-127">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ebfa9-128">Гиперболический тангенс (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-128">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="ebfa9-129">(Exp (x) – EXP (-x))/(exp (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-129">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ebfa9-130">Гиперболический секанс (Сеч (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-130">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="ebfa9-131">2/(exp (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-131">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ebfa9-132">Гиперболический косеканс (Ксч (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-132">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="ebfa9-133">2/(exp (x) — EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-133">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ebfa9-134">Гиперболический котангенс (КОС (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-134">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="ebfa9-135">(Exp (x) + EXP (-x))/(exp (x) – EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-135">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ebfa9-136">Обратный гиперболический синус (Asinh (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-136">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="ebfa9-137">Log (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-137">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="ebfa9-138">Обратный гиперболический косинус (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-138">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="ebfa9-139">Log (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-139">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ebfa9-140">Обратный гиперболический тангенс (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-140">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="ebfa9-141">Журнал ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-141">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="ebfa9-142">Обратный гиперболический секанс (Асеч (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-142">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="ebfa9-143">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-143">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ebfa9-144">Обратный гиперболический косеканс (Аксч (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-144">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="ebfa9-145">Log ((знак (x) \* SQRT (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-145">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ebfa9-146">Обратный гиперболический котангенс (Акос (x))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-146">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="ebfa9-147">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-147">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebfa9-148">См. также</span><span class="sxs-lookup"><span data-stu-id="ebfa9-148">See also</span></span>

- [<span data-ttu-id="ebfa9-149">Математические функции</span><span class="sxs-lookup"><span data-stu-id="ebfa9-149">Math Functions</span></span>](../functions/math-functions.md)
