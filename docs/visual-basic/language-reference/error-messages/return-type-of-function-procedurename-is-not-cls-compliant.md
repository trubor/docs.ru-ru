---
description: 'Дополнительные сведения о: BC40027: тип возвращаемого значения функции "" несовместим с <procedurename> CLS'
title: Тип возвращаемого значения функции <procedurename> несовместим с CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: df0cdb10ebc62a833cef89d3e82bc1ed756c556e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675121"
---
# <a name="bc40027-return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="2f1ca-103">BC40027: тип возвращаемого значения функции "" несовместим с \<procedurename> CLS</span><span class="sxs-lookup"><span data-stu-id="2f1ca-103">BC40027: Return type of function '\<procedurename>' is not CLS-compliant</span></span>

<span data-ttu-id="2f1ca-104">`Function`Процедура помечена как `<CLSCompliant(True)>` , но возвращает тип, помеченный как `<CLSCompliant(False)>` , не помечен или не может быть указан, поскольку является несоответствующим типом.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-104">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>

 <span data-ttu-id="2f1ca-105">Для соответствия требованиям, описанным в статье [Независимость от языка и независимые от языка компоненты](../../../standard/language-independence-and-language-independent-components.md) (CLS), процедура должна использовать только типы, совместимые с CLS.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="2f1ca-106">Это касается типов параметров, типа возвращаемого значения и типов всех локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>

 <span data-ttu-id="2f1ca-107">Следующие типы данных Visual Basic несовместимы с CLS:</span><span class="sxs-lookup"><span data-stu-id="2f1ca-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="2f1ca-108">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="2f1ca-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="2f1ca-109">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="2f1ca-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="2f1ca-110">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="2f1ca-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="2f1ca-111">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="2f1ca-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="2f1ca-112">При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-112">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="2f1ca-113">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-113">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="2f1ca-114">Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-114">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="2f1ca-115">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-115">By default, this message is a warning.</span></span> <span data-ttu-id="2f1ca-116">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2f1ca-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="2f1ca-117">**Идентификатор ошибки:** BC40027</span><span class="sxs-lookup"><span data-stu-id="2f1ca-117">**Error ID:** BC40027</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2f1ca-118">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="2f1ca-118">To correct this error</span></span>

- <span data-ttu-id="2f1ca-119">Если `Function` процедура должна возвращать этот конкретный тип, удалите <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2f1ca-119">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="2f1ca-120">Процедура не может быть совместимой с CLS.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-120">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="2f1ca-121">Если `Function` процедура должна быть совместимой с CLS, измените тип возвращаемого значения на ближайший CLS-совместимый тип.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-121">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="2f1ca-122">Например, вместо `UInteger` вы можете использовать `Integer` , если вам не нужен диапазон значений, превышающий 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="2f1ca-123">Если вам нужен расширенный диапазон, вы можете заменить `UInteger` на `Long`.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="2f1ca-124">При взаимоработе с автоматизацией или COM-объектами Помните, что некоторые типы имеют разную ширину данных, чем в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="2f1ca-125">Например, данные типа `int` часто являются 16-битными в других средах.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="2f1ca-126">Если вы возвращаете 16-разрядное целое число в такой компонент, объявите его как `Short` вместо `Integer` в управляемом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2f1ca-126">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
