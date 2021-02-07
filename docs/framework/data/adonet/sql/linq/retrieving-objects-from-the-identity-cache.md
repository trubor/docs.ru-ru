---
description: 'Дополнительные сведения: получение объектов из кэша удостоверений'
title: Извлечение объектов из кэша идентификации
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 1f3d5f839a6fff33d62d4e0cb2281bd087f2d320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695090"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="0cec1-103">Извлечение объектов из кэша идентификации</span><span class="sxs-lookup"><span data-stu-id="0cec1-103">Retrieving Objects from the Identity Cache</span></span>

<span data-ttu-id="0cec1-104">В этом разделе описаны типы запросов LINQ to SQL, которые возвращают объект из кэша идентификаторов, управляемого <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="0cec1-104">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="0cec1-105">В LINQ to SQL в качестве одного из способов управления объектами <xref:System.Data.Linq.DataContext> регистрируют идентификаторы объектов в кэше идентификаторов во время выполнения запросов.</span><span class="sxs-lookup"><span data-stu-id="0cec1-105">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="0cec1-106">В некоторых случаях LINQ to SQL пытается получить объект из кэша идентификаторов перед выполнением запроса в базе данных.</span><span class="sxs-lookup"><span data-stu-id="0cec1-106">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="0cec1-107">Обычно, чтобы запрос LINQ to SQL мог вернуть объект из кэша идентификаторов, запрос должен быть основан на первичном ключе объекта и должен возвращать одиночный объект.</span><span class="sxs-lookup"><span data-stu-id="0cec1-107">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="0cec1-108">В частности, запрос должен иметь одну из общих форм, представленных далее.</span><span class="sxs-lookup"><span data-stu-id="0cec1-108">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cec1-109">Предварительно скомпилированные запросы не возвращают объекты из кэша идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="0cec1-109">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="0cec1-110">Дополнительные сведения о предварительно скомпилированных запросах см <xref:System.Data.Linq.CompiledQuery> . [в разделе и инструкции. Хранение и повторное использование запросов](how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0cec1-110">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="0cec1-111">Чтобы получить объект из кэша идентификаторов, запрос должен иметь одну из следующих общих форм.</span><span class="sxs-lookup"><span data-stu-id="0cec1-111">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="0cec1-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="0cec1-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="0cec1-113"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="0cec1-113"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="0cec1-114">В этих общих формах параметры `Function1`, `Function2` и `predicate` определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0cec1-114">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="0cec1-115">Параметр `Function1` может иметь любое из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="0cec1-115">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="0cec1-116">Параметр `Function2` может иметь любое из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="0cec1-116">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="0cec1-117">Параметр `predicate` должен быть выражением, в котором свойство первичного ключа объекта устанавливается в постоянное значение.</span><span class="sxs-lookup"><span data-stu-id="0cec1-117">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="0cec1-118">Если первичный ключ определен в нескольких свойствах объекта, то в каждом свойстве должно быть задано постоянное значение.</span><span class="sxs-lookup"><span data-stu-id="0cec1-118">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="0cec1-119">Далее представлены примеры формы, которую должен принимать параметр `predicate`.</span><span class="sxs-lookup"><span data-stu-id="0cec1-119">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="0cec1-120">Пример</span><span class="sxs-lookup"><span data-stu-id="0cec1-120">Example</span></span>  

 <span data-ttu-id="0cec1-121">В следующем коде приводятся примеры типов запросов LINQ to SQL, которые получают объект из кэша идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="0cec1-121">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0cec1-122">См. также</span><span class="sxs-lookup"><span data-stu-id="0cec1-122">See also</span></span>

- [<span data-ttu-id="0cec1-123">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="0cec1-123">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="0cec1-124">Идентификация объектов</span><span class="sxs-lookup"><span data-stu-id="0cec1-124">Object Identity</span></span>](object-identity.md)
- [<span data-ttu-id="0cec1-125">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="0cec1-125">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="0cec1-126">Идентификация объектов</span><span class="sxs-lookup"><span data-stu-id="0cec1-126">Object Identity</span></span>](object-identity.md)
