---
description: Дополнительные сведения см. в статье как вызывать пользовательские функции базы данных.
title: Практическое руководство. Вызов настраиваемых функций базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f33630f68740877ff2d0e7f0fec7202453d96bf7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696793"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="4537b-103">Практическое руководство. Вызов настраиваемых функций базы данных</span><span class="sxs-lookup"><span data-stu-id="4537b-103">How to: Call Custom Database Functions</span></span>

<span data-ttu-id="4537b-104">В данном разделе описаны процедуры вызова пользовательских функций, определенных в базе данных, из запросов LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4537b-104">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>

<span data-ttu-id="4537b-105">Функции базы данных, вызываемые в запросах LINQ to Entities, выполняются в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-105">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="4537b-106">При выполнении функций в базе данных может увеличиться производительность приложений.</span><span class="sxs-lookup"><span data-stu-id="4537b-106">Executing functions in the database can improve application performance.</span></span>

<span data-ttu-id="4537b-107">Процедура, приведенная ниже, обеспечивает высокоуровневую структуру вызова пользовательской функции базы данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-107">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="4537b-108">В следующем примере подробно описаны шаги данной процедуры.</span><span class="sxs-lookup"><span data-stu-id="4537b-108">The example that follows provides more detail about the steps in the procedure.</span></span>

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="4537b-109">Вызов пользовательских функций, определенных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-109">To call custom functions that are defined in the database</span></span>

1. <span data-ttu-id="4537b-110">Создайте пользовательскую функцию в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-110">Create a custom function in your database.</span></span>

     <span data-ttu-id="4537b-111">Дополнительные сведения о создании пользовательских функций в SQL Server см. в разделе [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="4537b-111">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span></span>

2. <span data-ttu-id="4537b-112">Объявите функцию на языке SSDL в EDMX-файле.</span><span class="sxs-lookup"><span data-stu-id="4537b-112">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="4537b-113">Имя функции должно совпадать с именем функции, объявленной в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-113">The name of the function must be the same as the name of the function declared in the database.</span></span>

     <span data-ttu-id="4537b-114">Дополнительные сведения см. в разделе [элемент Function (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="4537b-114">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>

3. <span data-ttu-id="4537b-115">Добавьте соответствующий метод к классу в коде приложения и примените <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> к этому методу. Обратите внимание, что параметры атрибута <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> и <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> представляют собой имя пространства имен концептуальной модели и имя функции концептуальной модели соответственно.</span><span class="sxs-lookup"><span data-stu-id="4537b-115">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="4537b-116">При разрешении имени функции для LINQ учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="4537b-116">Function name resolution for LINQ is case sensitive.</span></span>

4. <span data-ttu-id="4537b-117">Вызовите метод в запросе LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4537b-117">Call the method in a LINQ to Entities query.</span></span>  

## <a name="example"></a><span data-ttu-id="4537b-118">Пример</span><span class="sxs-lookup"><span data-stu-id="4537b-118">Example</span></span>

<span data-ttu-id="4537b-119">В следующем примере показываются процедуры вызова пользовательской функции базы данных из запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4537b-119">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="4537b-120">В этом примере используется модель School.</span><span class="sxs-lookup"><span data-stu-id="4537b-120">The example uses the School model.</span></span> <span data-ttu-id="4537b-121">Сведения о модели School см. в разделе [Создание образца базы данных School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) и [Создание файла School. EDMX](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4537b-121">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>

<span data-ttu-id="4537b-122">Следующий код добавляет функцию `AvgStudentGrade` в образец базы данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-122">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>

> [!NOTE]
> <span data-ttu-id="4537b-123">Шаги вызова пользовательской функции базы данных одинаковы, независимо от сервера базы данных.</span><span class="sxs-lookup"><span data-stu-id="4537b-123">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="4537b-124">Однако следующий код предназначен специально для создания функции в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4537b-124">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="4537b-125">Код для создания пользовательской функции на других серверах баз данных может отличаться.</span><span class="sxs-lookup"><span data-stu-id="4537b-125">The code for creating a custom function in other database servers might differ.</span></span>

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a><span data-ttu-id="4537b-126">Пример</span><span class="sxs-lookup"><span data-stu-id="4537b-126">Example</span></span>

<span data-ttu-id="4537b-127">Затем объявите функцию на языке SSDL для *EDMX* -файла.</span><span class="sxs-lookup"><span data-stu-id="4537b-127">Next, declare a function in the store schema definition language (SSDL) of your *.edmx* file.</span></span> <span data-ttu-id="4537b-128">Следующий код объявляет `AvgStudentGrade` функцию на языке SSDL:</span><span class="sxs-lookup"><span data-stu-id="4537b-128">The following code declares the `AvgStudentGrade` function in SSDL:</span></span>

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a><span data-ttu-id="4537b-129">Пример</span><span class="sxs-lookup"><span data-stu-id="4537b-129">Example</span></span>

<span data-ttu-id="4537b-130">Теперь создайте метод и сопоставьте его с функцией, объявленной в SSDL.</span><span class="sxs-lookup"><span data-stu-id="4537b-130">Now, create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="4537b-131">Метод в следующем классе сопоставляется с функцией, определенной на языке SSDL (выше) с помощью <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4537b-131">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="4537b-132">При вызове этого метода в базе данных выполняется соответствующая функция.</span><span class="sxs-lookup"><span data-stu-id="4537b-132">When this method is called, the corresponding function in the database is executed.</span></span>

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="4537b-133">Пример</span><span class="sxs-lookup"><span data-stu-id="4537b-133">Example</span></span>

<span data-ttu-id="4537b-134">Наконец, вызовите метод в запросе LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4537b-134">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="4537b-135">Следующий код отображает в консоли фамилии студентов и средние баллы:</span><span class="sxs-lookup"><span data-stu-id="4537b-135">The following code displays students' last names and average grades to the console:</span></span>

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="4537b-136">См. также</span><span class="sxs-lookup"><span data-stu-id="4537b-136">See also</span></span>

- <span data-ttu-id="4537b-137">[Общие сведения о EDMX-файлах](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4537b-137">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="4537b-138">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4537b-138">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
