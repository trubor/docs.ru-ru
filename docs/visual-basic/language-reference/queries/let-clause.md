---
description: 'Дополнительные сведения: предложение let (Visual Basic)'
title: Предложение Let
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88a7d96bb790a1e6ec5adfa4337c51f807930168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653645"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="e2918-103">Предложение Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2918-103">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="e2918-104">Выполняет вычисление значения и присваивает его новой переменной в запросе.</span><span class="sxs-lookup"><span data-stu-id="e2918-104">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2918-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e2918-105">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="e2918-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="e2918-106">Parts</span></span>  
  
|<span data-ttu-id="e2918-107">Термин</span><span class="sxs-lookup"><span data-stu-id="e2918-107">Term</span></span>|<span data-ttu-id="e2918-108">Определение</span><span class="sxs-lookup"><span data-stu-id="e2918-108">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="e2918-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="e2918-109">Required.</span></span> <span data-ttu-id="e2918-110">Псевдоним, который может использоваться для ссылки на результаты предоставляемого выражения.</span><span class="sxs-lookup"><span data-stu-id="e2918-110">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="e2918-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e2918-111">Required.</span></span> <span data-ttu-id="e2918-112">Выражение, которое будет вычислено и назначено указанной переменной.</span><span class="sxs-lookup"><span data-stu-id="e2918-112">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2918-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="e2918-113">Remarks</span></span>  

 <span data-ttu-id="e2918-114">`Let`Предложение позволяет вычислять значения для каждого результата запроса и ссылаться на них с помощью псевдонима.</span><span class="sxs-lookup"><span data-stu-id="e2918-114">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="e2918-115">Псевдоним можно использовать в других предложениях, например в `Where` предложении.</span><span class="sxs-lookup"><span data-stu-id="e2918-115">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="e2918-116">`Let`Предложение позволяет создать инструкцию запроса, которая будет проще читать, поскольку можно указать псевдоним для предложения выражения, включенного в запрос, и заменить псевдоним при каждом использовании предложения Expression.</span><span class="sxs-lookup"><span data-stu-id="e2918-116">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="e2918-117">В предложение можно включить любое количество `variable` `expression` назначений и `Let` .</span><span class="sxs-lookup"><span data-stu-id="e2918-117">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="e2918-118">Разделяйте каждое назначение запятой (,).</span><span class="sxs-lookup"><span data-stu-id="e2918-118">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2918-119">Пример</span><span class="sxs-lookup"><span data-stu-id="e2918-119">Example</span></span>  

 <span data-ttu-id="e2918-120">В следующем примере кода предложение используется `Let` для расчета скидки на 10% для продуктов.</span><span class="sxs-lookup"><span data-stu-id="e2918-120">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="e2918-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e2918-121">See also</span></span>

- <span data-ttu-id="e2918-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2918-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="e2918-123">Запросы</span><span class="sxs-lookup"><span data-stu-id="e2918-123">Queries</span></span>](index.md)
- [<span data-ttu-id="e2918-124">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="e2918-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e2918-125">Предложение From</span><span class="sxs-lookup"><span data-stu-id="e2918-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e2918-126">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="e2918-126">Where Clause</span></span>](where-clause.md)
