---
description: 'Дополнительные сведения: автоматические реализуемые свойства (Visual Basic)'
title: Автоматически реализуемые свойства
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 61f6565f9d4e7ea8731bb09c59cd6d942ab8c129
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472700"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="32dce-103">Автоматически реализуемые свойства (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32dce-103">Auto-Implemented Properties (Visual Basic)</span></span>

<span data-ttu-id="32dce-104">*Автоматические реализованные свойства* позволяют быстро указывать свойство класса без необходимости написания кода для `Get` и `Set` Свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-104">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="32dce-105">При написании кода для автоматически реализуемого свойства компилятор Visual Basic автоматически создает закрытое поле для хранения переменной свойства, в дополнение к созданию связанных процедур `Get` и `Set`.</span><span class="sxs-lookup"><span data-stu-id="32dce-105">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="32dce-106">С помощью автоматически реализуемых свойств вы сможете объявлять свойства, включая значение по умолчанию, в одной строке.</span><span class="sxs-lookup"><span data-stu-id="32dce-106">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="32dce-107">В следующем примере показано три объявления свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-107">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="32dce-108">Автоматически реализуемые свойства эквивалентны свойствам, значения которых хранятся в закрытом поле.</span><span class="sxs-lookup"><span data-stu-id="32dce-108">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="32dce-109">В следующем примере кода показано автоматически реализуемое свойство.</span><span class="sxs-lookup"><span data-stu-id="32dce-109">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="32dce-110">В следующем примере кода показан эквивалентный код для предыдущего примера автоматически реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-110">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="32dce-111">В следующем примере кода показана реализация свойств только для чтения:</span><span class="sxs-lookup"><span data-stu-id="32dce-111">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="32dce-112">Вы можете назначить свойству выражения инициализации, как показано в примере, или можно присвоить значения свойствам в конструкторе этого типа.</span><span class="sxs-lookup"><span data-stu-id="32dce-112">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="32dce-113">Резервные поля свойств только для чтения можно назначить в любое время.</span><span class="sxs-lookup"><span data-stu-id="32dce-113">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="32dce-114">Резервное поле</span><span class="sxs-lookup"><span data-stu-id="32dce-114">Backing Field</span></span>  

 <span data-ttu-id="32dce-115">При объявлении автоматически реализуемого свойства Visual Basic автоматически создает скрытое закрытое поле, называемое *резервным полем* , которое содержит значение свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-115">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="32dce-116">Имя резервного поля — это имя автоматически реализуемого свойства, с добавленным в начало знаком подчеркивания (_).</span><span class="sxs-lookup"><span data-stu-id="32dce-116">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="32dce-117">Например, при объявлении автоматически реализуемого свойства с именем `ID` именем резервного поля будет `_ID`.</span><span class="sxs-lookup"><span data-stu-id="32dce-117">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="32dce-118">Если добавить элемент класса также с именем `_ID`, возникнет конфликт имен, и Visual Basic сообщает об ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="32dce-118">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="32dce-119">Резервное поле также имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="32dce-119">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="32dce-120">модификатор доступа для резервного поля — всегда `Private`, даже если само свойство имеет другой уровень доступа, например `Public`;</span><span class="sxs-lookup"><span data-stu-id="32dce-120">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="32dce-121">если свойство помечено как `Shared`, резервное поле также будет общим;</span><span class="sxs-lookup"><span data-stu-id="32dce-121">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="32dce-122">атрибуты, указанные для свойства, не применяются к резервному полю;</span><span class="sxs-lookup"><span data-stu-id="32dce-122">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="32dce-123">доступ к резервному полю можно получить из кода внутри класса и из средств отладки, например окна контрольных значений.</span><span class="sxs-lookup"><span data-stu-id="32dce-123">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="32dce-124">Однако резервное поле не отображается в списке предложений IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="32dce-124">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="32dce-125">Инициализация автоматически реализуемого свойства</span><span class="sxs-lookup"><span data-stu-id="32dce-125">Initializing an Auto-Implemented Property</span></span>  

 <span data-ttu-id="32dce-126">Любое выражение, которое может использоваться для инициализации поля, можно применять для инициализации автоматически реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-126">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="32dce-127">При инициализации автоматически реализуемого свойства выражение анализируется и передается процедуре `Set` для свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-127">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="32dce-128">В следующих примерах кода показаны некоторые автоматически реализуемые свойства с начальными значениями.</span><span class="sxs-lookup"><span data-stu-id="32dce-128">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="32dce-129">Невозможно инициализировать автоматически реализуемое свойство, которое является элементом `Interface` или помечено как `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="32dce-129">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="32dce-130">При объявлении автоматически реализуемого свойства как элемента `Structure` его можно инициализировать, только если оно помечено как `Shared`.</span><span class="sxs-lookup"><span data-stu-id="32dce-130">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="32dce-131">При объявлении автоматически реализуемого свойства как массива невозможно указать явные границы массива.</span><span class="sxs-lookup"><span data-stu-id="32dce-131">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="32dce-132">Однако можно задать значение с помощью инициализатора массива, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="32dce-132">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="32dce-133">Определения свойств, для которых требуется стандартный синтаксис</span><span class="sxs-lookup"><span data-stu-id="32dce-133">Property Definitions That Require Standard Syntax</span></span>  

 <span data-ttu-id="32dce-134">Автоматически реализуемые свойства удобны и поддерживают множество сценариев программирования.</span><span class="sxs-lookup"><span data-stu-id="32dce-134">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="32dce-135">Однако существуют ситуации, в которых нельзя использовать автоматическое реализуемое свойство и вместо этого использовать стандартный или *Расширенный* синтаксис свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-135">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="32dce-136">Расширенный синтаксис определения свойства необходимо использовать, если вам нужно выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="32dce-136">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="32dce-137">Добавить код для процедуры `Get` или `Set` свойства, например для проверки входящих значений в процедуре `Set`.</span><span class="sxs-lookup"><span data-stu-id="32dce-137">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="32dce-138">Например, вам требуется убедиться, что строка, представляющая номер телефона, содержит необходимое количество цифр перед заданием значения свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-138">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="32dce-139">Указать другой уровень доступа для процедуры `Get` и `Set`.</span><span class="sxs-lookup"><span data-stu-id="32dce-139">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="32dce-140">Например, вам может потребоваться сделать процедуру `Set``Private`, а процедуру `Get` — `Public`.</span><span class="sxs-lookup"><span data-stu-id="32dce-140">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="32dce-141">Создать свойства типа `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="32dce-141">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="32dce-142">Использовать параметризованные свойства (включая `Default`).</span><span class="sxs-lookup"><span data-stu-id="32dce-142">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="32dce-143">Чтобы задать параметр для свойства или указать дополнительные параметры, требуется объявить развернутое свойство процедуры `Set`.</span><span class="sxs-lookup"><span data-stu-id="32dce-143">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="32dce-144">Добавить атрибут в резервное поле или изменить уровень доступа резервного поля.</span><span class="sxs-lookup"><span data-stu-id="32dce-144">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="32dce-145">Добавить XML-комментарии для резервного поля.</span><span class="sxs-lookup"><span data-stu-id="32dce-145">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="32dce-146">Расширение автоматически реализуемого свойства</span><span class="sxs-lookup"><span data-stu-id="32dce-146">Expanding an Auto-Implemented Property</span></span>  

 <span data-ttu-id="32dce-147">Если вам требуется преобразовать автоматически реализуемое свойство в расширенное свойство, которое содержит процедуру `Get` или `Set`, редактор кода Visual Basic может автоматически создать процедуры `Get` и `Set` и оператор `End Property` для свойства.</span><span class="sxs-lookup"><span data-stu-id="32dce-147">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="32dce-148">Код создается при помещении курсора на пустую строку после `Property` оператора, введите a `G` (для `Get` ) или `S` (для `Set` ) и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="32dce-148">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="32dce-149">Редактор кода Visual Basic автоматически создает процедуру `Get` или `Set` для свойств только для чтения и только для записи при нажатии клавиши ВВОД после оператора `Property`.</span><span class="sxs-lookup"><span data-stu-id="32dce-149">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32dce-150">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="32dce-150">See also</span></span>

- [<span data-ttu-id="32dce-151">Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32dce-151">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="32dce-152">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="32dce-152">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="32dce-153">Property Statement</span><span class="sxs-lookup"><span data-stu-id="32dce-153">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="32dce-154">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="32dce-154">ReadOnly</span></span>](../../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="32dce-155">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="32dce-155">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="32dce-156">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="32dce-156">Objects and Classes</span></span>](../objects-and-classes/index.md)
