---
description: 'Дополнительные сведения: функция, объявленная моделью'
title: объявляемая моделью функция
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9a5cedb8c9706aa0d299635f60f762b92ca6d78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786268"
---
# <a name="model-declared-function"></a><span data-ttu-id="c1e9d-103">объявляемая моделью функция</span><span class="sxs-lookup"><span data-stu-id="c1e9d-103">model-declared function</span></span>

<span data-ttu-id="c1e9d-104">*Объявленная моделью функция* — это функция, объявленная в концептуальной модели, но не определенная в этой концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-104">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="c1e9d-105">Функция может быть определена в среде размещения или хранения.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-105">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="c1e9d-106">Например, объявляемая моделью функция может быть сопоставлена функции, определенной в базе данных, экспонируя таким образом функцию в концептуальной модели на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-106">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="c1e9d-107">Объявление объявляемой моделью функции содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-107">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="c1e9d-108">Имя функции.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-108">The name of the function.</span></span> <span data-ttu-id="c1e9d-109">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="c1e9d-109">(Required)</span></span>  
  
- <span data-ttu-id="c1e9d-110">Тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-110">The type of the return value.</span></span> <span data-ttu-id="c1e9d-111">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="c1e9d-111">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1e9d-112">Если возвращаемое значение не задано, возвращаемого значения не будет.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-112">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="c1e9d-113">Сведения о параметрах, включая имя и тип параметров.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-113">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="c1e9d-114">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="c1e9d-114">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1e9d-115">Пример</span><span class="sxs-lookup"><span data-stu-id="c1e9d-115">Example</span></span>  

 <span data-ttu-id="c1e9d-116">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-116">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="c1e9d-117">В языке CSDL одна реализация функции, объявленной в модели, является импортом функции (с помощью [элемента FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="c1e9d-117">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="c1e9d-118">Далее на языке CSDL определяется контейнер сущностей с определением импорта функции.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-118">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="c1e9d-119">Обратите внимание, что возвращаемый тип для функции отсутствует, поскольку возвращаемый тип не задан.</span><span class="sxs-lookup"><span data-stu-id="c1e9d-119">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="c1e9d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c1e9d-120">See also</span></span>

- [<span data-ttu-id="c1e9d-121">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="c1e9d-121">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="c1e9d-122">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="c1e9d-122">Entity Data Model</span></span>](entity-data-model.md)
