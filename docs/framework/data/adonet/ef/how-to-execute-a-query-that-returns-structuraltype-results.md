---
description: Дополнительные сведения см. в статье как выполнить запрос, возвращающий результаты Структуралтипе.
title: Практическое руководство. Выполнение запроса, возвращающего результаты типа StructuralType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: a5666fd84ed7253b58cc49babdfa5f5e4614146c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697547"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="84be5-103">Практическое руководство. Выполнение запроса, возвращающего результаты типа StructuralType</span><span class="sxs-lookup"><span data-stu-id="84be5-103">How to: Execute a Query that Returns StructuralType Results</span></span>

<span data-ttu-id="84be5-104">В этом подразделе показано выполнение команды для концептуальной модели с помощью объекта <xref:System.Data.EntityClient.EntityCommand>, а также получение результатов <xref:System.Data.Metadata.Edm.StructuralType> с помощью <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="84be5-104">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="84be5-105">Классы <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> и <xref:System.Data.Metadata.Edm.ComplexType> являются производными класса <xref:System.Data.Metadata.Edm.StructuralType>.</span><span class="sxs-lookup"><span data-stu-id="84be5-105">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="84be5-106">Выполнение кода в этом примере</span><span class="sxs-lookup"><span data-stu-id="84be5-106">To run the code in this example</span></span>  
  
1. <span data-ttu-id="84be5-107">Добавьте [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) в проект и настройте проект для использования Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="84be5-107">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="84be5-108">Дополнительные сведения см. в разделе [инструкции. Использование мастера EDM](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="84be5-108">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="84be5-109">На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="84be5-109">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="84be5-110">Пример</span><span class="sxs-lookup"><span data-stu-id="84be5-110">Example</span></span>  

 <span data-ttu-id="84be5-111">В этом примере выполняется запрос, который возвращает результаты <xref:System.Data.Metadata.Edm.EntityType>.</span><span class="sxs-lookup"><span data-stu-id="84be5-111">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="84be5-112">При передаче следующего запроса в качестве аргумента функции `ExecuteStructuralTypeQuery` функция отобразит подробные сведения о `Products`:</span><span class="sxs-lookup"><span data-stu-id="84be5-112">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="84be5-113">Передавая параметризованный запрос, подобный следующему, добавьте объекты <xref:System.Data.EntityClient.EntityParameter> к свойству <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> объекта <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="84be5-113">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="84be5-114">См. также</span><span class="sxs-lookup"><span data-stu-id="84be5-114">See also</span></span>

- [<span data-ttu-id="84be5-115">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="84be5-115">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="84be5-116">Поставщик EntityClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="84be5-116">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
