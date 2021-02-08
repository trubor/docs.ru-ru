---
description: 'Дополнительные сведения: оператор End <keyword> (Visual Basic)'
title: Оператор End <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: ba21d4ba68a054d77d4f29307d49ed8e82bb6b50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769199"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="aeee5-103">Оператор End \<keyword> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aeee5-103">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="aeee5-104">Если за ним следует дополнительное ключевое слово, завершает определение блока операторов, представленного этим ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="aeee5-104">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="aeee5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aeee5-105">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="aeee5-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="aeee5-106">Parts</span></span>

|<span data-ttu-id="aeee5-107">Отделение</span><span class="sxs-lookup"><span data-stu-id="aeee5-107">Part</span></span>|<span data-ttu-id="aeee5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="aeee5-108">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="aeee5-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="aeee5-109">Required.</span></span> <span data-ttu-id="aeee5-110">Завершает определение программного элемента.</span><span class="sxs-lookup"><span data-stu-id="aeee5-110">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="aeee5-111">Требуется для завершения `AddHandler` метода доступа, начатого соответствующим `AddHandler` оператором в пользовательской [инструкции Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-111">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="aeee5-112">Требуется для завершения определения класса, начатого соответствующим [оператором класса](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-112">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="aeee5-113">Требуется для завершения определения перечисления, начатого соответствующей [инструкцией enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-113">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="aeee5-114">Требуется для завершения `Custom` определения события, начатого соответствующей [инструкцией Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-114">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="aeee5-115">Требуется для завершения `Function` определения процедуры, начатой соответствующей [инструкцией Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-115">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="aeee5-116">Если выполнение встречает `End Function` оператор, управление возвращается в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="aeee5-116">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="aeee5-117">Требуется для завершения `Property` определения процедуры, начатой соответствующей [инструкцией GET](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-117">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="aeee5-118">Если выполнение встречает `End Get` оператор, управление возвращается инструкции, запрашивающей значение свойства.</span><span class="sxs-lookup"><span data-stu-id="aeee5-118">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="aeee5-119">Требуется для завершения `If` ... `Then` ...`Else` блок определения, начатого соответствующим `If` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-119">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="aeee5-120">См. раздел [If... Затем... Else, инструкция](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-120">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="aeee5-121">Требуется для завершения определения интерфейса, начатого соответствующей [инструкцией интерфейса](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-121">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="aeee5-122">Требуется для завершения определения модуля, начатого соответствующим [оператором модуля](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-122">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="aeee5-123">Требуется для завершения определения пространства имен, начатого соответствующей [инструкцией Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-123">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="aeee5-124">Требуется для завершения определения оператора, начатого соответствующим [оператором оператора](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-124">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="aeee5-125">Требуется для завершения определения свойства, начатого соответствующим [оператором Property](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-125">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="aeee5-126">Требуется для завершения `RaiseEvent` метода доступа, начатого соответствующим `RaiseEvent` оператором в пользовательской [инструкции Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-126">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="aeee5-127">Требуется для завершения `RemoveHandler` метода доступа, начатого соответствующим `RemoveHandler` оператором в пользовательской [инструкции Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-127">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="aeee5-128">Требуется для завершения `Select` определения блока..., `Case` начатого соответствующим `Select` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-128">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="aeee5-129">См. раздел [SELECT... Case, инструкция](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-129">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="aeee5-130">Требуется для завершения `Property` определения процедуры, начатой соответствующей [инструкцией SET](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-130">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="aeee5-131">Если выполнение встречает `End Set` оператор, управление возвращается в инструкцию, устанавливая значение свойства.</span><span class="sxs-lookup"><span data-stu-id="aeee5-131">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="aeee5-132">Требуется для завершения определения структуры, начатой соответствующей [инструкцией Structure](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-132">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="aeee5-133">Требуется для завершения `Sub` определения процедуры, начатой соответствующим [подоператором](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-133">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="aeee5-134">Если выполнение встречает `End Sub` оператор, управление возвращается в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="aeee5-134">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="aeee5-135">Требуется для завершения `SyncLock` определения блока, начатого соответствующим `SyncLock` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-135">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="aeee5-136">См. раздел [оператор SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-136">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="aeee5-137">Требуется для завершения `Try` ... `Catch` ...`Finally` блок определения, начатого соответствующим `Try` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-137">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="aeee5-138">См [. раздел try... Перехватить... Оператор finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-138">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="aeee5-139">Требуется для завершения `While` определения цикла, начатого соответствующим `While` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-139">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="aeee5-140">См [. раздел while... Конец оператора while](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-140">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="aeee5-141">Требуется для завершения `With` определения блока, начатого соответствующим `With` оператором.</span><span class="sxs-lookup"><span data-stu-id="aeee5-141">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="aeee5-142">См [. раздел with... Конец оператора](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-142">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="aeee5-143">Директивы</span><span class="sxs-lookup"><span data-stu-id="aeee5-143">Directives</span></span>

<span data-ttu-id="aeee5-144">Если перед ним стоит знак решетки ( `#` ), `End` ключевое слово завершает блок предварительной обработки, представленный соответствующей директивой.</span><span class="sxs-lookup"><span data-stu-id="aeee5-144">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="aeee5-145">Отделение</span><span class="sxs-lookup"><span data-stu-id="aeee5-145">Part</span></span>|<span data-ttu-id="aeee5-146">Описание</span><span class="sxs-lookup"><span data-stu-id="aeee5-146">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="aeee5-147">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="aeee5-147">Required.</span></span> <span data-ttu-id="aeee5-148">Завершает определение блока предварительной обработки.</span><span class="sxs-lookup"><span data-stu-id="aeee5-148">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="aeee5-149">Требуется для завершения внешнего блока источника, начатого соответствующей [директивой #ExternalSource](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-149">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="aeee5-150">Требуется для завершения блока условной компиляции, начатого соответствующей `#If` директивой.</span><span class="sxs-lookup"><span data-stu-id="aeee5-150">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="aeee5-151">См [. #If... Then... #Else директивы](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-151">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="aeee5-152">Требуется для завершения блока исходного региона, начатого соответствующей [директивой #Region](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="aeee5-152">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="aeee5-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="aeee5-153">Remarks</span></span>

<span data-ttu-id="aeee5-154">[Оператор End](end-statement.md)без дополнительного ключевого слова завершает выполнение немедленно.</span><span class="sxs-lookup"><span data-stu-id="aeee5-154">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="aeee5-155">Примечания для разработчиков смарт-устройств</span><span class="sxs-lookup"><span data-stu-id="aeee5-155">Smart Device Developer Notes</span></span>  

<span data-ttu-id="aeee5-156">`End`Инструкция без дополнительного ключевого слова не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="aeee5-156">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeee5-157">См. также</span><span class="sxs-lookup"><span data-stu-id="aeee5-157">See also</span></span>

- [<span data-ttu-id="aeee5-158">End, инструкция</span><span class="sxs-lookup"><span data-stu-id="aeee5-158">End Statement</span></span>](end-statement.md)
