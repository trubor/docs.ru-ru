---
description: 'Дополнительные сведения: Добавление бизнес-логики с помощью разделяемых методов'
title: Добавление бизнес-логики с использованием разделяемых методов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: c34d0d25fa9dba074f1c7ff2abe2e9e24c931a8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672274"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="3824c-103">Добавление бизнес-логики с использованием разделяемых методов</span><span class="sxs-lookup"><span data-stu-id="3824c-103">Adding Business Logic By Using Partial Methods</span></span>

<span data-ttu-id="3824c-104">Можно настроить Visual Basic и код, созданный C#, в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проектах с помощью *разделяемых методов*.</span><span class="sxs-lookup"><span data-stu-id="3824c-104">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="3824c-105">Код, созданный [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], определяет сигнатуры как одну часть разделяемого метода.</span><span class="sxs-lookup"><span data-stu-id="3824c-105">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="3824c-106">Если необходимо реализовать метод, можно добавить собственный разделяемый метод.</span><span class="sxs-lookup"><span data-stu-id="3824c-106">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="3824c-107">Если собственная реализация не добавляется, компилятор отменяет сигнатуру разделяемых методов и вызывает в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] методы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3824c-107">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3824c-108">При использовании Visual Studio можно использовать реляционный конструктор объектов для добавления проверки и других настроек в классы сущностей.</span><span class="sxs-lookup"><span data-stu-id="3824c-108">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="3824c-109">Например, применяемое по умолчанию сопоставление для класса `Customer` в образце базы данных Northwind включает следующий разделяемый метод:</span><span class="sxs-lookup"><span data-stu-id="3824c-109">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="3824c-110">Можно реализовать собственный метод путем добавления кода, подобного представленному далее, в собственный разделяемый класс `Customer`.</span><span class="sxs-lookup"><span data-stu-id="3824c-110">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="3824c-111">Этот подход обычно используется в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для переопределения методов по умолчанию для `Insert` ,, и `Update` `Delete` для проверки свойств во время событий жизненного цикла объекта.</span><span class="sxs-lookup"><span data-stu-id="3824c-111">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="3824c-112">Дополнительные сведения см. в разделе [разделяемые методы](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) или [partial (метод) (Справочник по c#](../../../../../csharp/language-reference/keywords/partial-method.md) ) (c#).</span><span class="sxs-lookup"><span data-stu-id="3824c-112">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3824c-113">Пример</span><span class="sxs-lookup"><span data-stu-id="3824c-113">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3824c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="3824c-114">Description</span></span>  

 <span data-ttu-id="3824c-115">В примере кода `ExampleClass` сначала отображается так, как если бы он был определен с помощью средства создания кода, например SQLMetal, а затем так, как при реализации только одного из двух методов.</span><span class="sxs-lookup"><span data-stu-id="3824c-115">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3824c-116">Код</span><span class="sxs-lookup"><span data-stu-id="3824c-116">Code</span></span>  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="3824c-117">Пример</span><span class="sxs-lookup"><span data-stu-id="3824c-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3824c-118">Описание</span><span class="sxs-lookup"><span data-stu-id="3824c-118">Description</span></span>  

 <span data-ttu-id="3824c-119">В следующем примере используется связь между сущностями `Shipper` и `Order`.</span><span class="sxs-lookup"><span data-stu-id="3824c-119">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="3824c-120">Среди прочих методов обратите внимание на разделяемые - `InsertShipper` и `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="3824c-120">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="3824c-121">Эти методы переопределяют разделяемые методы по умолчанию, предоставляемые [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="3824c-121">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3824c-122">Код</span><span class="sxs-lookup"><span data-stu-id="3824c-122">Code</span></span>  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3824c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="3824c-123">See also</span></span>

- [<span data-ttu-id="3824c-124">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="3824c-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="3824c-125">Настройка операций вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="3824c-125">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
