---
description: 'Дополнительные сведения: определяемая моделью функция'
title: функция определенной модели
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 146ef4a8ad8c38897b8e56b6bc1485e1e40754cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723742"
---
# <a name="model-defined-function"></a><span data-ttu-id="3adf2-103">функция определенной модели</span><span class="sxs-lookup"><span data-stu-id="3adf2-103">model-defined function</span></span>

<span data-ttu-id="3adf2-104">*Определяемая моделью функция* — это функция, определенная в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="3adf2-104">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="3adf2-105">Текст функции, определяемой моделью, выражается в [Entity SQL](./ef/language-reference/entity-sql-language.md), что позволяет выражать функцию независимо от правил или языков, поддерживаемых в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="3adf2-105">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="3adf2-106">Определение определяемой моделью функции содержит следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="3adf2-106">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="3adf2-107">Имя функции.</span><span class="sxs-lookup"><span data-stu-id="3adf2-107">A function name.</span></span> <span data-ttu-id="3adf2-108">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="3adf2-108">(Required)</span></span>  
  
- <span data-ttu-id="3adf2-109">Тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="3adf2-109">The type of the return value.</span></span> <span data-ttu-id="3adf2-110">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="3adf2-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3adf2-111">Если тип возвращаемого значения не задан, возвращаемого значения не будет.</span><span class="sxs-lookup"><span data-stu-id="3adf2-111">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="3adf2-112">Сведения о параметрах.</span><span class="sxs-lookup"><span data-stu-id="3adf2-112">Parameter information.</span></span> <span data-ttu-id="3adf2-113">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="3adf2-113">(Optional)</span></span>  
  
- <span data-ttu-id="3adf2-114">Выражение [Entity SQL](./ef/language-reference/entity-sql-language.md) , определяющее текст функции.</span><span class="sxs-lookup"><span data-stu-id="3adf2-114">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="3adf2-115">Обратите внимание, что определяемые моделью функции не поддерживают выходные параметры.</span><span class="sxs-lookup"><span data-stu-id="3adf2-115">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="3adf2-116">Это ограничение введено, чтобы определяемые моделью функции можно было сочетать.</span><span class="sxs-lookup"><span data-stu-id="3adf2-116">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3adf2-117">Пример</span><span class="sxs-lookup"><span data-stu-id="3adf2-117">Example</span></span>  

 <span data-ttu-id="3adf2-118">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="3adf2-118">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Снимок экрана, на котором показана модель с опубликованной датой.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="3adf2-120">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="3adf2-120">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="3adf2-121">Следующий язык CSDL определяет функцию в концептуальной модели, которая возвращает числа лет с момента публикации экземпляра `Book` (ранее приведенного на схеме).</span><span class="sxs-lookup"><span data-stu-id="3adf2-121">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="3adf2-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3adf2-122">See also</span></span>

- [<span data-ttu-id="3adf2-123">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="3adf2-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="3adf2-124">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="3adf2-124">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="3adf2-125">EDM (модель данных с использованием сущностей): примитивные типы данных</span><span class="sxs-lookup"><span data-stu-id="3adf2-125">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
