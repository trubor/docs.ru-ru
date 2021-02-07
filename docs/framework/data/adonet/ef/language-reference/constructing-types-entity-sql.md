---
description: 'Дополнительные сведения: создание типов (Entity SQL)'
title: Сборка типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 5963c34ffd8e9273d400cc16ba93f72ded2ede46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724847"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="cc23e-103">Сборка типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cc23e-103">Constructing Types (Entity SQL)</span></span>

<!-- markdownlint-disable DOCSMD001 -->
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="cc23e-104">предоставляет три вида конструкторов: конструкторы строк, конструкторы именованных типов и конструкторы коллекций.</span><span class="sxs-lookup"><span data-stu-id="cc23e-104">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>

## <a name="row-constructors"></a><span data-ttu-id="cc23e-105">Конструкторы строк</span><span class="sxs-lookup"><span data-stu-id="cc23e-105">Row Constructors</span></span>

<span data-ttu-id="cc23e-106">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] конструкторы строк можно использовать для создания анонимных структурно типизированных записей из одного или нескольких значений.</span><span class="sxs-lookup"><span data-stu-id="cc23e-106">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="cc23e-107">Результирующий тип конструктора строк является типом строки, типы полей которого соответствуют типам значений, использовавшихся для создания этой строки.</span><span class="sxs-lookup"><span data-stu-id="cc23e-107">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="cc23e-108">Например, следующее выражение конструирует значение типа `Record(a int, b string, c int)` :</span><span class="sxs-lookup"><span data-stu-id="cc23e-108">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>

`ROW(1 AS a, "abc" AS b, a + 34 AS c)`

<span data-ttu-id="cc23e-109">Если в конструкторе строк не указан псевдоним для выражения, то платформа Entity Framework попытается сформировать его.</span><span class="sxs-lookup"><span data-stu-id="cc23e-109">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="cc23e-110">Дополнительные сведения см. в разделе "правила присвоения псевдонимов" статьи [идентификаторы](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cc23e-110">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>

<span data-ttu-id="cc23e-111">В конструкторе строк псевдонимы присваиваются выражениям по следующим правилам.</span><span class="sxs-lookup"><span data-stu-id="cc23e-111">The following rules apply to expression aliasing in a row constructor:</span></span>

- <span data-ttu-id="cc23e-112">Выражение в конструкторе строк не может ссылаться на другие псевдонимы в этом же конструкторе.</span><span class="sxs-lookup"><span data-stu-id="cc23e-112">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>
- <span data-ttu-id="cc23e-113">Два выражения в одном конструкторе строк не могут иметь одинаковый псевдоним.</span><span class="sxs-lookup"><span data-stu-id="cc23e-113">Two expressions in the same row constructor cannot have the same alias.</span></span>

<span data-ttu-id="cc23e-114">Дополнительные сведения о конструкторах строк см. в разделе [Row](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cc23e-114">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>

## <a name="collection-constructors"></a><span data-ttu-id="cc23e-115">Конструкторы коллекций</span><span class="sxs-lookup"><span data-stu-id="cc23e-115">Collection Constructors</span></span>

<span data-ttu-id="cc23e-116">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] конструкторы коллекций можно использовать для создания экземпляра мультинабора из списка значений.</span><span class="sxs-lookup"><span data-stu-id="cc23e-116">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="cc23e-117">Все значения в конструкторе должны иметь взаимно совместимый тип `T`. Конструктор формирует коллекцию типа `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="cc23e-117">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="cc23e-118">Например, следующее выражение создает коллекцию целых чисел.</span><span class="sxs-lookup"><span data-stu-id="cc23e-118">For example, the following expression creates a collection of integers:</span></span>

`Multiset(1, 2, 3)`

`{1, 2, 3}`

<span data-ttu-id="cc23e-119">Конструкторы пустых мультинаборов не разрешены, так как в этом случае нельзя определить тип элементов.</span><span class="sxs-lookup"><span data-stu-id="cc23e-119">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="cc23e-120">Недопустимый мультинабор:</span><span class="sxs-lookup"><span data-stu-id="cc23e-120">The following is not valid:</span></span>

`multiset() {}`

<span data-ttu-id="cc23e-121">Дополнительные сведения см. в разделе [мультинабор](multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cc23e-121">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>

## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="cc23e-122">Конструкторы именованных типов (инициализаторы NamedType)</span><span class="sxs-lookup"><span data-stu-id="cc23e-122">Named Type Constructors (NamedType Initializers)</span></span>

<span data-ttu-id="cc23e-123">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] позволяет конструкторам типов (инициализаторам) создавать экземпляры именованных сложных типов и типов сущностей.</span><span class="sxs-lookup"><span data-stu-id="cc23e-123">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="cc23e-124">Например, следующее выражение создает экземпляр типа `Person`.</span><span class="sxs-lookup"><span data-stu-id="cc23e-124">For example, the following expression creates an instance of a `Person` type.</span></span>

`Person("abc", 12)`

<span data-ttu-id="cc23e-125">Приведенное далее выражение создает экземпляр сложного типа.</span><span class="sxs-lookup"><span data-stu-id="cc23e-125">The following expression creates an instance of a complex type.</span></span>

`MyModel.ZipCode(‘98118’, ‘4567’)`

<span data-ttu-id="cc23e-126">Приведенное далее выражение создает экземпляр вложенного сложного типа.</span><span class="sxs-lookup"><span data-stu-id="cc23e-126">The following expression creates an instance of a nested complex type.</span></span>

`MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`

<span data-ttu-id="cc23e-127">Приведенное далее выражение создает экземпляр сущности с вложенным сложным типом.</span><span class="sxs-lookup"><span data-stu-id="cc23e-127">The following expression creates an instance of an entity with a nested complex type.</span></span>

`MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`

<span data-ttu-id="cc23e-128">В следующем примере показано, как инициализировать свойство сложного типа значением null.</span><span class="sxs-lookup"><span data-stu-id="cc23e-128">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`

<span data-ttu-id="cc23e-129">Предполагается, что аргументы конструктора находятся в порядке, соответствующем порядку декларации атрибутов типа.</span><span class="sxs-lookup"><span data-stu-id="cc23e-129">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>

<span data-ttu-id="cc23e-130">Дополнительные сведения см. в разделе [Конструктор именованного типа](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cc23e-130">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc23e-131">См. также</span><span class="sxs-lookup"><span data-stu-id="cc23e-131">See also</span></span>

- [<span data-ttu-id="cc23e-132">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cc23e-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="cc23e-133">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cc23e-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="cc23e-134">Система типов</span><span class="sxs-lookup"><span data-stu-id="cc23e-134">Type System</span></span>](type-system-entity-sql.md)
