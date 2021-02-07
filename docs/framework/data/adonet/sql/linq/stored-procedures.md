---
description: 'Дополнительные сведения: хранимые процедуры'
title: Хранимые процедуры
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 16157dc5a8d2da880deb2d43b649b872d19c73a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681439"
---
# <a name="stored-procedures"></a><span data-ttu-id="3c611-103">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="3c611-103">Stored Procedures</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3c611-104">использует методы в объектной модели для представления хранимых процедур в базе данных.</span><span class="sxs-lookup"><span data-stu-id="3c611-104">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="3c611-105">Чтобы задать методы в качестве хранимых процедур, следует применить атрибут <xref:System.Data.Linq.Mapping.FunctionAttribute> и, где необходимо, атрибут <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3c611-105">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="3c611-106">Дополнительные сведения см. [в разделе Объектная модель LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="3c611-106">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="3c611-107">Разработчики, использующие Visual Studio, обычно используют реляционный конструктор объектов для отображения хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="3c611-107">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="3c611-108">В темах данного раздела показано формирование и вызов этих методов в приложении при самостоятельном написании кода.</span><span class="sxs-lookup"><span data-stu-id="3c611-108">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c611-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="3c611-109">In This Section</span></span>  

 [<span data-ttu-id="3c611-110">Практическое руководство. Как возвращать наборы строк</span><span class="sxs-lookup"><span data-stu-id="3c611-110">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="3c611-111">Содержит сведения о возвращении строк данных и об использовании входного параметра.</span><span class="sxs-lookup"><span data-stu-id="3c611-111">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="3c611-112">Практическое руководство. Как использовать хранимые процедуры, которые принимают параметры</span><span class="sxs-lookup"><span data-stu-id="3c611-112">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="3c611-113">Содержит сведения об использовании входных и выходных параметров.</span><span class="sxs-lookup"><span data-stu-id="3c611-113">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="3c611-114">Практическое руководство. Как использовать хранимые процедуры, сопоставленные с несколькими результирующими формами</span><span class="sxs-lookup"><span data-stu-id="3c611-114">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="3c611-115">Содержит сведения о предоставлении возвратов нескольких фигур в одной хранимой процедуре.</span><span class="sxs-lookup"><span data-stu-id="3c611-115">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="3c611-116">Практическое руководство. Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами</span><span class="sxs-lookup"><span data-stu-id="3c611-116">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="3c611-117">Содержит сведения о предоставлении нескольких фигур при наличии известной возвращаемой последовательности.</span><span class="sxs-lookup"><span data-stu-id="3c611-117">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="3c611-118">Настройка операций за счет хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="3c611-118">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="3c611-119">Содержит описание использования хранимых процедур для выполнения операций вставки, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="3c611-119">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="3c611-120">Настройка операций за счет исключительного использования хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="3c611-120">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="3c611-121">Содержит описание использования только хранимых процедур для выполнения операций вставки, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="3c611-121">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c611-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3c611-122">Related Sections</span></span>  

 [<span data-ttu-id="3c611-123">Руководство по программированию</span><span class="sxs-lookup"><span data-stu-id="3c611-123">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="3c611-124">Содержит сведения о создании и использовании объектной модели [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c611-124">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="3c611-125">Пошаговое руководство. Применение только хранимых процедур (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c611-125">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="3c611-126">Содержит процедуры, в которых показано использование хранимых процедур в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3c611-126">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="3c611-127">Пошаговое руководство. Применение только хранимых процедур (C#)</span><span class="sxs-lookup"><span data-stu-id="3c611-127">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="3c611-128">Содержит процедуры, в которых показано использование хранимых процедур в C#.</span><span class="sxs-lookup"><span data-stu-id="3c611-128">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
