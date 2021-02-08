---
description: 'Дополнительные сведения см. в статье как создать объектную модель в Visual Basic или C. #'
title: Практическое руководство. Как создать модель объектов на языке Visual Basic или C#
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: d842a646f9f6186d252d10297618ddc2cb137e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785969"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="a186c-103">Как создать объектную модель в Visual Basic или C\#</span><span class="sxs-lookup"><span data-stu-id="a186c-103">How to: Generate the Object Model in Visual Basic or C\#</span></span>

<span data-ttu-id="a186c-104">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектная модель используемого языка программирования сопоставляется с реляционной базой данных.</span><span class="sxs-lookup"><span data-stu-id="a186c-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="a186c-105">Доступны два средства для автоматического создания Visual Basic или модели C# на основе метаданных существующей базы данных.</span><span class="sxs-lookup"><span data-stu-id="a186c-105">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="a186c-106">При использовании Visual Studio можно использовать реляционный конструктор объектов для создания объектной модели.</span><span class="sxs-lookup"><span data-stu-id="a186c-106">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="a186c-107">Реляционный конструктор объектов (R) предоставляет богатый пользовательский интерфейс, помогающий в создании [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектной модели.</span><span class="sxs-lookup"><span data-stu-id="a186c-107">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="a186c-108">Дополнительные сведения см. [в разделе средства LINQ to SQL в Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="a186c-108">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="a186c-109">Средство командной строки SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a186c-109">The SQLMetal command-line tool.</span></span> <span data-ttu-id="a186c-110">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a186c-110">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a186c-111">Если существующие базы данных отсутствуют и необходимо создать базу данных из объектной модели, можно создать объектную модель с помощью редактора кода и метода <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="a186c-111">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="a186c-112">Дополнительные сведения см. [в разделе инструкции. динамическое создание базы данных](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="a186c-112">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="a186c-113">Документация для реляционного конструктора объектов (R) содержит примеры создания объектной модели Visual Basic или C# с помощью конструктора O/R.</span><span class="sxs-lookup"><span data-stu-id="a186c-113">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="a186c-114">Ниже приведены примеры использования программы командной строки SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a186c-114">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="a186c-115">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a186c-115">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a186c-116">Пример</span><span class="sxs-lookup"><span data-stu-id="a186c-116">Example</span></span>  

 <span data-ttu-id="a186c-117">Командная строка SQLMetal, показанная в следующем примере, создает Visual Basic код в качестве объектной модели на основе атрибутов образца базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="a186c-117">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a186c-118">Также отображаются хранимые процедуры и функции.</span><span class="sxs-lookup"><span data-stu-id="a186c-118">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="a186c-119">Пример</span><span class="sxs-lookup"><span data-stu-id="a186c-119">Example</span></span>  

 <span data-ttu-id="a186c-120">С помощью команды программы SQLMetal, представленной в следующем примере, создается код C# для основанной на атрибутах объектной модели базы данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="a186c-120">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a186c-121">Также отображаются хранимые процедуры и функции и имена таблиц автоматически преобразуются в имена во множественном числе.</span><span class="sxs-lookup"><span data-stu-id="a186c-121">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a186c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a186c-122">See also</span></span>

- [<span data-ttu-id="a186c-123">Руководство по программированию</span><span class="sxs-lookup"><span data-stu-id="a186c-123">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="a186c-124">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a186c-124">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a186c-125">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="a186c-125">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="a186c-126">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="a186c-126">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="a186c-127">Сопоставление, основанное на атрибутах</span><span class="sxs-lookup"><span data-stu-id="a186c-127">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="a186c-128">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="a186c-128">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="a186c-129">Внешнее сопоставление</span><span class="sxs-lookup"><span data-stu-id="a186c-129">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="a186c-130">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="a186c-130">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="a186c-131">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="a186c-131">Creating the Object Model</span></span>](creating-the-object-model.md)
