---
description: Дополнительные сведения см. в статье как определить тип, на который ссылается объектная переменная (Visual Basic)
title: Практическое руководство. Определение типа, на который указывает объектная переменная
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 699a8c5c075fc923a61a66f617c255f193cd8797
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481926"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="dbd5f-103">Практическое руководство. Определение типа, на который указывает объектная переменная (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbd5f-103">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="dbd5f-104">Объектная переменная содержит указатель на данные, которые хранятся в других местах.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-104">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="dbd5f-105">Тип этих данных может изменяться во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-105">The type of that data can change during run time.</span></span> <span data-ttu-id="dbd5f-106">В любой момент можно использовать <xref:System.Type.GetTypeCode%2A> метод для определения текущего типа времени выполнения или [оператор typeof](../../../language-reference/operators/typeof-operator.md) , чтобы определить, совместим ли текущий тип времени выполнения с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-106">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="dbd5f-107">Определение точного типа объектной переменной, на которую в настоящее время ссылается</span><span class="sxs-lookup"><span data-stu-id="dbd5f-107">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="dbd5f-108">В объектной переменной вызовите <xref:System.Object.GetType%2A> метод, чтобы получить <xref:System.Type?displayProperty=nameWithType> объект.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-108">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="dbd5f-109">В <xref:System.Type?displayProperty=nameWithType> классе вызовите метод Shared, <xref:System.Type.GetTypeCode%2A> чтобы получить <xref:System.TypeCode> значение перечисления для типа объекта.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-109">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="dbd5f-110">Можно проверить <xref:System.TypeCode> значение перечисления в отношении любого интересующего его члена, например `Double` .</span><span class="sxs-lookup"><span data-stu-id="dbd5f-110">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="dbd5f-111">Определение, совместима ли тип объектной переменной с указанным типом</span><span class="sxs-lookup"><span data-stu-id="dbd5f-111">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="dbd5f-112">Используйте `TypeOf` оператор в сочетании с [оператором is](../../../language-reference/operators/is-operator.md) для проверки объекта с помощью выражения. `TypeOf` .. `Is`</span><span class="sxs-lookup"><span data-stu-id="dbd5f-112">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="dbd5f-113">`TypeOf`Выражение... `Is` возвращает значение, `True` Если тип времени выполнения объекта совместим с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-113">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="dbd5f-114">Критерий совместимости зависит от того, является ли указанный тип классом, структурой или интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-114">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="dbd5f-115">Как правило, типы являются совместимыми, если объект имеет тот же тип, что и, наследует от или реализует указанный тип.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-115">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="dbd5f-116">Дополнительные сведения см. в разделе [оператор typeof](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="dbd5f-116">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="dbd5f-117">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="dbd5f-117">Compile the code</span></span>

<span data-ttu-id="dbd5f-118">Обратите внимание, что указанный тип не может быть переменной или выражением.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-118">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="dbd5f-119">Это должно быть имя определенного типа, например класса, структуры или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="dbd5f-119">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="dbd5f-120">Сюда входят встроенные типы, такие как `Integer` и `String` .</span><span class="sxs-lookup"><span data-stu-id="dbd5f-120">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbd5f-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dbd5f-121">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="dbd5f-122">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="dbd5f-122">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="dbd5f-123">Значения объектных переменных</span><span class="sxs-lookup"><span data-stu-id="dbd5f-123">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="dbd5f-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="dbd5f-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
