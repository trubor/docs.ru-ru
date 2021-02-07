---
description: Дополнительные сведения о канонических функциях
title: Канонические функции
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 6e84c4b5199d38e2efac44cf7e69c72abb1663f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739512"
---
# <a name="canonical-functions"></a><span data-ttu-id="279fa-103">Канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-103">Canonical Functions</span></span>

<span data-ttu-id="279fa-104">В этом разделе обсуждаются канонические функции, которые поддерживаются всеми поставщиками данных и могут использоваться всеми технологиями запросов.</span><span class="sxs-lookup"><span data-stu-id="279fa-104">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="279fa-105">Канонические функции не могут расширяться поставщиком.</span><span class="sxs-lookup"><span data-stu-id="279fa-105">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="279fa-106">Эти канонические функции будут преобразованы в соответствующие функции источника данных для поставщика.</span><span class="sxs-lookup"><span data-stu-id="279fa-106">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="279fa-107">Это позволит формулировать вызовы функций в формате, общем для разных источников данных.</span><span class="sxs-lookup"><span data-stu-id="279fa-107">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="279fa-108">Эти канонические функции не зависят от типа источника данных, поэтому для них типы аргументов и возвращаемых значений определяются в терминах типов, доступных в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="279fa-108">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="279fa-109">Однако некоторые источники данных поддерживают не все типы в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="279fa-109">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="279fa-110">При использовании в запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] канонической функции будет вызвана соответствующая функция в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="279fa-110">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="279fa-111">Во всех канонических функциях явным образом определяется обработка входных значений NULL и условия возникновения ошибок.</span><span class="sxs-lookup"><span data-stu-id="279fa-111">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="279fa-112">Поставщики хранилища должны соответствовать этому поведению, но Entity Framework не применяет это поведение.</span><span class="sxs-lookup"><span data-stu-id="279fa-112">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="279fa-113">В сценариях LINQ запросы к Entity Framework содержат сопоставление методов CLR с методами в базовом источнике данных.</span><span class="sxs-lookup"><span data-stu-id="279fa-113">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="279fa-114">Методы CLR сопоставляются с каноническими функциями, и поэтому правильное сопоставление возможно для любого набора методов, независимо от источника данных.</span><span class="sxs-lookup"><span data-stu-id="279fa-114">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="279fa-115">Пространство имен канонических функций</span><span class="sxs-lookup"><span data-stu-id="279fa-115">Canonical Functions Namespace</span></span>  

 <span data-ttu-id="279fa-116">Для канонических функций выделено пространство имен <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="279fa-116">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="279fa-117">Пространство имен <xref:System.Data.Metadata.Edm> автоматически включается во все запросы.</span><span class="sxs-lookup"><span data-stu-id="279fa-117">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="279fa-118">Однако при импорте другого пространства имен, в котором содержится функция с именем, совпадающим с именем канонической функции (из пространства имен <xref:System.Data.Metadata.Edm>), то пространство имен необходимо указывать явным образом.</span><span class="sxs-lookup"><span data-stu-id="279fa-118">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="279fa-119">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="279fa-119">In This Section</span></span>  

 [<span data-ttu-id="279fa-120">Статистические канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-120">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="279fa-121">Обсуждаются статистические канонические функции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-121">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-122">Математические канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-122">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="279fa-123">Обсуждаются математические канонические функции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-123">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-124">Строковые канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-124">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="279fa-125">Обсуждаются строковые канонические функции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-125">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-126">Канонические функции даты и времени</span><span class="sxs-lookup"><span data-stu-id="279fa-126">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="279fa-127">Обсуждаются канонические функции даты и времени в языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-127">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-128">Битовые канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-128">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="279fa-129">Обсуждаются побитовые канонические функции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-129">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-130">Пространственные функции</span><span class="sxs-lookup"><span data-stu-id="279fa-130">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="279fa-131">Рассматриваются пространственные канонические функции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="279fa-131">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="279fa-132">Прочие канонические функции</span><span class="sxs-lookup"><span data-stu-id="279fa-132">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="279fa-133">Обсуждаются функции, которые не являются побитовыми, строковыми, математическими, статистическими или функциями даты-времени.</span><span class="sxs-lookup"><span data-stu-id="279fa-133">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279fa-134">См. также</span><span class="sxs-lookup"><span data-stu-id="279fa-134">See also</span></span>

- [<span data-ttu-id="279fa-135">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="279fa-135">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="279fa-136">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="279fa-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="279fa-137">Сопоставление канонических функций концептуальной модели с функциями SQL Server</span><span class="sxs-lookup"><span data-stu-id="279fa-137">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="279fa-138">Определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="279fa-138">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
