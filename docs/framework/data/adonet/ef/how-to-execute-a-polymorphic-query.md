---
description: Дополнительные сведения о том, как выполнить преформацию запроса.
title: Практическое руководство. Выполнение полиморфного запроса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 02074fb0ad60e5ba8d62094e25f35db40f8a2dbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650746"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="b5331-103">Практическое руководство. Выполнение полиморфного запроса</span><span class="sxs-lookup"><span data-stu-id="b5331-103">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="b5331-104">В этом разделе показано, как выполнить преформацию [!INCLUDE[esql](../../../../../includes/esql-md.md)] запроса с помощью оператора [OFTYPE](./language-reference/oftype-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="b5331-104">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b5331-105">Выполнение кода в этом примере</span><span class="sxs-lookup"><span data-stu-id="b5331-105">To run the code in this example</span></span>

1. <span data-ttu-id="b5331-106">Добавьте [модель School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) в проект и настройте проект для использования Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b5331-106">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="b5331-107">Дополнительные сведения см. в разделе [инструкции. Использование мастера EDM](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5331-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="b5331-108">На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="b5331-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="b5331-109">Измените концептуальную модель так, чтобы она была наследована с одной таблицей на иерархию, выполнив действия, описанные в [разделе Пошаговое руководство. сопоставление наследования-таблица-иерархия](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5331-109">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="b5331-110">Пример</span><span class="sxs-lookup"><span data-stu-id="b5331-110">Example</span></span>

<span data-ttu-id="b5331-111">В следующем примере используется оператор OFTYPE для возврата и отображения коллекции только элементов `OnsiteCourses` из коллекции `Courses`.</span><span class="sxs-lookup"><span data-stu-id="b5331-111">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="b5331-112">См. также</span><span class="sxs-lookup"><span data-stu-id="b5331-112">See also</span></span>

- [<span data-ttu-id="b5331-113">Поставщик EntityClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b5331-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="b5331-114">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b5331-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
