---
description: 'Дополнительные сведения: конструктор именованного типа (Entity SQL)'
title: Конструктор именованных типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: e5ec811f814898661cf8de28de1fb8406647332d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696546"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="6751f-103">Конструктор именованных типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6751f-103">Named Type Constructor (Entity SQL)</span></span>

<span data-ttu-id="6751f-104">Используется для создания экземпляров номинальных типов концептуальной модели, например сложных типов или типов сущностей.</span><span class="sxs-lookup"><span data-stu-id="6751f-104">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6751f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6751f-105">Syntax</span></span>  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6751f-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="6751f-106">Arguments</span></span>  

 `identifier`  
 <span data-ttu-id="6751f-107">Значение, представляющее собой простой или заключенный в кавычки идентификатор.</span><span class="sxs-lookup"><span data-stu-id="6751f-107">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="6751f-108">Дополнительные сведения см. в разделе [идентификаторы](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6751f-108">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="6751f-109">Атрибуты типа, которые, как предполагается, должны располагаться в таком же порядке, как и в декларации этого типа.</span><span class="sxs-lookup"><span data-stu-id="6751f-109">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6751f-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6751f-110">Return Value</span></span>  

 <span data-ttu-id="6751f-111">Экземпляры именованных сложных типов и типов сущностей.</span><span class="sxs-lookup"><span data-stu-id="6751f-111">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6751f-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="6751f-112">Remarks</span></span>  

 <span data-ttu-id="6751f-113">В следующих примерах показано, как создавать номинальные и сложные типы.</span><span class="sxs-lookup"><span data-stu-id="6751f-113">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="6751f-114">Приведенное далее выражение создает экземпляр типа `Person` .</span><span class="sxs-lookup"><span data-stu-id="6751f-114">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="6751f-115">Приведенное далее выражение создает экземпляр сложного типа.</span><span class="sxs-lookup"><span data-stu-id="6751f-115">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="6751f-116">Приведенное далее выражение создает экземпляр вложенного сложного типа.</span><span class="sxs-lookup"><span data-stu-id="6751f-116">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="6751f-117">Приведенное далее выражение создает экземпляр сущности с вложенным сложным типом.</span><span class="sxs-lookup"><span data-stu-id="6751f-117">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="6751f-118">В следующем примере показано, как инициализировать свойство сложного типа значением null:`MyModel.ZipCode(‘98118’, null)`.</span><span class="sxs-lookup"><span data-stu-id="6751f-118">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="6751f-119">Пример</span><span class="sxs-lookup"><span data-stu-id="6751f-119">Example</span></span>  

 <span data-ttu-id="6751f-120">В следующем запросе Entity SQL конструктор именованного типа используется для создания экземпляра типа концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="6751f-120">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="6751f-121">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="6751f-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6751f-122">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="6751f-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6751f-123">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6751f-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6751f-124">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="6751f-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="6751f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="6751f-125">See also</span></span>

- [<span data-ttu-id="6751f-126">Сборка типов</span><span class="sxs-lookup"><span data-stu-id="6751f-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="6751f-127">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6751f-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
