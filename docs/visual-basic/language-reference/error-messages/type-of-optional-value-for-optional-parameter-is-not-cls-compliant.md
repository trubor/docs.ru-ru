---
description: 'Дополнительные сведения о: BC40042: Тип необязательного значения для необязательного параметра несовместим с <parametername> CLS'
title: Тип необязательного значения для необязательного параметра <parametername> несовместим с CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 44dee07120ebcd99be69257aef6a334f9067cdb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774867"
---
# <a name="bc40042-type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="969f9-103">BC40042: Тип необязательного значения для необязательного параметра несовместим с \<parametername> CLS</span><span class="sxs-lookup"><span data-stu-id="969f9-103">BC40042: Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>

<span data-ttu-id="969f9-104">Процедура помечена как `<CLSCompliant(True)>`, но она объявляет [необязательный](../modifiers/optional.md) параметр со значением по умолчанию несовместимого типа.</span><span class="sxs-lookup"><span data-stu-id="969f9-104">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>

 <span data-ttu-id="969f9-105">Для соответствия требованиям, описанным в статье [Независимость от языка и независимые от языка компоненты](../../../standard/language-independence-and-language-independent-components.md) (CLS), процедура должна использовать только типы, совместимые с CLS.</span><span class="sxs-lookup"><span data-stu-id="969f9-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="969f9-106">Это касается типов параметров, типа возвращаемого значения и типов всех локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="969f9-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="969f9-107">Это также касается значений по умолчанию для необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="969f9-107">It also applies to the default values of optional parameters.</span></span>

 <span data-ttu-id="969f9-108">Следующие типы данных Visual Basic несовместимы с CLS:</span><span class="sxs-lookup"><span data-stu-id="969f9-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="969f9-109">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="969f9-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="969f9-110">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="969f9-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="969f9-111">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="969f9-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="969f9-112">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="969f9-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="969f9-113">Когда вы применяете атрибут <xref:System.CLSCompliantAttribute> к программному элементу, вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать на соответствие или несоответствие требованиям.</span><span class="sxs-lookup"><span data-stu-id="969f9-113">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="969f9-114">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="969f9-114">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="969f9-115">Если вы не примените <xref:System.CLSCompliantAttribute> к элементу, он считается несоответствующим требованиям.</span><span class="sxs-lookup"><span data-stu-id="969f9-115">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="969f9-116">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="969f9-116">By default, this message is a warning.</span></span> <span data-ttu-id="969f9-117">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="969f9-117">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="969f9-118">**Идентификатор ошибки:** BC40042</span><span class="sxs-lookup"><span data-stu-id="969f9-118">**Error ID:** BC40042</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="969f9-119">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="969f9-119">To correct this error</span></span>

- <span data-ttu-id="969f9-120">Если необязательный параметр должен иметь значение по умолчанию для этого конкретного типа, удалите <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="969f9-120">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="969f9-121">Процедура не может быть совместимой с CLS.</span><span class="sxs-lookup"><span data-stu-id="969f9-121">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="969f9-122">Если процедура должна быть совместимой с CLS, измените тип этого значения по умолчанию на ближайший тип, совместимый с CLS.</span><span class="sxs-lookup"><span data-stu-id="969f9-122">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="969f9-123">Например, вместо `UInteger` вы можете использовать `Integer` , если вам не нужен диапазон значений, превышающий 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="969f9-123">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="969f9-124">Если вам нужен расширенный диапазон, вы можете заменить `UInteger` на `Long`.</span><span class="sxs-lookup"><span data-stu-id="969f9-124">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="969f9-125">При взаимоработе с автоматизацией или COM-объектами Помните, что некоторые типы имеют разную ширину данных, чем в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="969f9-125">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="969f9-126">Например, данные типа `int` часто являются 16-битными в других средах.</span><span class="sxs-lookup"><span data-stu-id="969f9-126">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="969f9-127">Если вы принимаете 16-разрядное целое число из такого компонента, объявите его как `Short` вместо `Integer` в управляемом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="969f9-127">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
