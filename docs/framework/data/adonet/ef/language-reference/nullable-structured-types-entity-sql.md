---
description: 'Дополнительные сведения: структурированные типы, допускающие значения NULL (Entity SQL)'
title: Допускающие значения null структурированные типы (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: bf303c9cd61fad2c2a8ffedf338bb3a8876db27b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802090"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="008f7-103">Допускающие значения null структурированные типы (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="008f7-103">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="008f7-104">Экземпляр `null` структурированного типа - несуществующий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="008f7-104">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="008f7-105">Это отличается от существующего экземпляра, все свойства которого имеют значения `null`.</span><span class="sxs-lookup"><span data-stu-id="008f7-105">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="008f7-106">В этом разделе описаны структурированные типы, допускающие значение NULL, с указанием, какие типы допускают значение NULL и какие последовательности программного кода формируют экземпляры `null` структурированных типов, допускающих значение NULL.</span><span class="sxs-lookup"><span data-stu-id="008f7-106">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="008f7-107">Разновидности структурированных типов, допускающих значение NULL</span><span class="sxs-lookup"><span data-stu-id="008f7-107">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="008f7-108">Существует три вида типов структуры, допускающих значения NULL:</span><span class="sxs-lookup"><span data-stu-id="008f7-108">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="008f7-109">Типы строк.</span><span class="sxs-lookup"><span data-stu-id="008f7-109">Row types.</span></span>  
  
- <span data-ttu-id="008f7-110">Сложные типы.</span><span class="sxs-lookup"><span data-stu-id="008f7-110">Complex types.</span></span>  
  
- <span data-ttu-id="008f7-111">Типы сущностей.</span><span class="sxs-lookup"><span data-stu-id="008f7-111">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="008f7-112">Шаблоны кода, которые формируют экземпляры NULL структурированных типов</span><span class="sxs-lookup"><span data-stu-id="008f7-112">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="008f7-113">В следующем сценарии формируются экземпляры `null`:</span><span class="sxs-lookup"><span data-stu-id="008f7-113">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="008f7-114">Формирование `null` как структурированного типа:</span><span class="sxs-lookup"><span data-stu-id="008f7-114">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="008f7-115">Приведение базового типа к производному типу:</span><span class="sxs-lookup"><span data-stu-id="008f7-115">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="008f7-116">Внешнее соединение по условию FALSE:</span><span class="sxs-lookup"><span data-stu-id="008f7-116">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="008f7-117">--или</span><span class="sxs-lookup"><span data-stu-id="008f7-117">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="008f7-118">--или</span><span class="sxs-lookup"><span data-stu-id="008f7-118">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="008f7-119">Разыменование ссылки на `null`:</span><span class="sxs-lookup"><span data-stu-id="008f7-119">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="008f7-120">Получение значения ANYELEMENT из пустой коллекции:</span><span class="sxs-lookup"><span data-stu-id="008f7-120">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="008f7-121">Проверка наличия экземпляров `null` структурированных типов:</span><span class="sxs-lookup"><span data-stu-id="008f7-121">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="008f7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="008f7-122">See also</span></span>

- [<span data-ttu-id="008f7-123">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="008f7-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
