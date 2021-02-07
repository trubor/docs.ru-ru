---
description: Дополнительные сведения см. в статье как вызывать функции Model-Defined в запросах.
title: Практическое руководство. Вызов определенных моделью функций в запросах
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: d59ef6edeba1e4b00e0481f8578e9c04735831fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748652"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="04d3a-103">Практическое руководство. Вызов определенных моделью функций в запросах</span><span class="sxs-lookup"><span data-stu-id="04d3a-103">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="04d3a-104">В этом разделе описывается вызов функций, определенных в концептуальной модели, из запросов LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="04d3a-104">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="04d3a-105">В приведенной ниже процедуре представлен общий обзор вызова определяемой моделью функции из LINQ to Entities запроса.</span><span class="sxs-lookup"><span data-stu-id="04d3a-105">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="04d3a-106">В следующем примере подробно описаны шаги данной процедуры.</span><span class="sxs-lookup"><span data-stu-id="04d3a-106">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="04d3a-107">Для этой процедуры предполагается, что функция была определена в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="04d3a-107">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="04d3a-108">Дополнительные сведения см. в разделе [инструкции. Определение пользовательских функций в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="04d3a-108">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="04d3a-109">Вызов функции, определенной в концептуальной модели</span><span class="sxs-lookup"><span data-stu-id="04d3a-109">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="04d3a-110">Добавьте в приложение метод среды CLR, который сопоставляется с функцией, определенной в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="04d3a-110">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="04d3a-111">Для сопоставления метода к нему необходимо применить атрибут <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="04d3a-111">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="04d3a-112">Обратите внимание, что параметры атрибута <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> и <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> представляют имя пространства имен концептуальной модели и имя функции концептуальной модели соответственно.</span><span class="sxs-lookup"><span data-stu-id="04d3a-112">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="04d3a-113">При разрешении имени функции для LINQ учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="04d3a-113">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="04d3a-114">Вызовите функцию в запросе LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="04d3a-114">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d3a-115">Пример</span><span class="sxs-lookup"><span data-stu-id="04d3a-115">Example</span></span>  

 <span data-ttu-id="04d3a-116">В следующем примере показано, как вызвать функцию, определенную в концептуальной модели, из запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="04d3a-116">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="04d3a-117">В этом примере используется модель School.</span><span class="sxs-lookup"><span data-stu-id="04d3a-117">The example uses the School model.</span></span> <span data-ttu-id="04d3a-118">Сведения о модели School см. в разделе [Создание образца базы данных School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) и [Создание файла School. EDMX](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="04d3a-118">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="04d3a-119">В следующей концептуальной модели функция возвращает сведения о количестве лет, истекших с момента приема инструктора на работу.</span><span class="sxs-lookup"><span data-stu-id="04d3a-119">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="04d3a-120">Дополнительные сведения о добавлении функции в концептуальную модель см. в разделе [инструкции. Определение пользовательских функций в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="04d3a-120">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="04d3a-121">Пример</span><span class="sxs-lookup"><span data-stu-id="04d3a-121">Example</span></span>  

 <span data-ttu-id="04d3a-122">Затем добавьте в приложение следующий метод и с помощью атрибута <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> сопоставьте его с функцией концептуальной модели:</span><span class="sxs-lookup"><span data-stu-id="04d3a-122">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="04d3a-123">Пример</span><span class="sxs-lookup"><span data-stu-id="04d3a-123">Example</span></span>  

 <span data-ttu-id="04d3a-124">Теперь можно вызвать функцию концептуальной модели из LINQ to Entities запроса.</span><span class="sxs-lookup"><span data-stu-id="04d3a-124">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="04d3a-125">Следующий код вызывает метод, чтобы отобразить всех инструкторов, которые были приняты на работу более десяти лет назад:</span><span class="sxs-lookup"><span data-stu-id="04d3a-125">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="04d3a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="04d3a-126">See also</span></span>

- <span data-ttu-id="04d3a-127">[Общие сведения о EDMX-файлах](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="04d3a-127">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="04d3a-128">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="04d3a-128">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="04d3a-129">Вызов функций в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="04d3a-129">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="04d3a-130">Практическое руководство. Вызов определенных моделью функций как методов объектов</span><span class="sxs-lookup"><span data-stu-id="04d3a-130">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
