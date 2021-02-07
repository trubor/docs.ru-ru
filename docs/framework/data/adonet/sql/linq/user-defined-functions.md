---
description: 'Дополнительные сведения: функции User-Defined'
title: Определяемые пользователем функции
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: d27abd78e15ad6cb5ce4e9440ac425159a0b5bdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680945"
---
# <a name="user-defined-functions"></a><span data-ttu-id="9b59c-103">Определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="9b59c-103">User-Defined Functions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9b59c-104">использует методы в объектной модели для представления пользовательских функций.</span><span class="sxs-lookup"><span data-stu-id="9b59c-104">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="9b59c-105">Чтобы назначить методы в качестве функций, следует применить атрибут <xref:System.Data.Linq.Mapping.FunctionAttribute>, а где необходимо - атрибут <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9b59c-105">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="9b59c-106">Дополнительные сведения см. [в разделе Объектная модель LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="9b59c-106">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="9b59c-107">Чтобы избежать <xref:System.InvalidOperationException>, пользовательские функции в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] должны быть представлены в одной из следующих форм.</span><span class="sxs-lookup"><span data-stu-id="9b59c-107">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="9b59c-108">Функция, упакованная в качестве вызова метода с правильными атрибутами сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9b59c-108">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="9b59c-109">Дополнительные сведения см. в разделе [сопоставление на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9b59c-109">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="9b59c-110">Статический метод SQL, характерный для [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b59c-110">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="9b59c-111">Функция, поддерживаемая методом платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b59c-111">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="9b59c-112">В темах данного раздела показано формирование и вызов этих методов в приложении при самостоятельном написании кода.</span><span class="sxs-lookup"><span data-stu-id="9b59c-112">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="9b59c-113">Разработчики, использующие Visual Studio, обычно используют реляционный конструктор объектов для соотнесения определяемых пользователем функций.</span><span class="sxs-lookup"><span data-stu-id="9b59c-113">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b59c-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="9b59c-114">In This Section</span></span>  

 [<span data-ttu-id="9b59c-115">Практическое руководство. Как применять определяемые пользователем скалярные функции</span><span class="sxs-lookup"><span data-stu-id="9b59c-115">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="9b59c-116">Описано, как реализовать функцию, возвращающую скалярные значения.</span><span class="sxs-lookup"><span data-stu-id="9b59c-116">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="9b59c-117">Практическое руководство. Как применять определяемые пользователем возвращающие табличное значение функции</span><span class="sxs-lookup"><span data-stu-id="9b59c-117">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="9b59c-118">Содержит описание способов реализации функции, возвращающей табличные значения.</span><span class="sxs-lookup"><span data-stu-id="9b59c-118">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="9b59c-119">Практическое руководство. Как вызывать встроенные определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="9b59c-119">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="9b59c-120">Содержит описание преобразования встроенных вызовов в функции и представляет различия при внутреннем осуществлении вызова.</span><span class="sxs-lookup"><span data-stu-id="9b59c-120">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
