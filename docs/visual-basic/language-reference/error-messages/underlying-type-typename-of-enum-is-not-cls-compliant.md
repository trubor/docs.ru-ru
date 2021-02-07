---
description: 'Дополнительные сведения о: BC40032: базовый тип <typename> перечисления несовместим с CLS'
title: Базовый тип <typename> перечисления несовместим с CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: aebee5a9e0cd7f2e780d0171ad59dcfd4fd1d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674796"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="58882-103">BC40032: базовый тип \<typename> перечисления несовместим с CLS</span><span class="sxs-lookup"><span data-stu-id="58882-103">BC40032: Underlying type \<typename> of Enum is not CLS-compliant</span></span>

<span data-ttu-id="58882-104">Тип данных, указанный для этого перечисления, не входит в [независимость от языка и Language-Independent компонентов](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="58882-104">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="58882-105">Это не ошибка в компоненте, так как платформа .NET Framework и Visual Basic поддерживают этот тип данных.</span><span class="sxs-lookup"><span data-stu-id="58882-105">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="58882-106">Однако другой компонент, написанный в строго CLS-совместимом коде, может не поддерживать этот тип данных.</span><span class="sxs-lookup"><span data-stu-id="58882-106">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="58882-107">Такой компонент, возможно, не сможет успешно взаимодействовать с компонентом.</span><span class="sxs-lookup"><span data-stu-id="58882-107">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="58882-108">Следующие типы данных Visual Basic несовместимы с CLS:</span><span class="sxs-lookup"><span data-stu-id="58882-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="58882-109">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="58882-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="58882-110">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="58882-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="58882-111">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="58882-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="58882-112">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="58882-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="58882-113">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="58882-113">By default, this message is a warning.</span></span> <span data-ttu-id="58882-114">Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="58882-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="58882-115">**Идентификатор ошибки:** BC40032</span><span class="sxs-lookup"><span data-stu-id="58882-115">**Error ID:** BC40032</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="58882-116">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="58882-116">To correct this error</span></span>

- <span data-ttu-id="58882-117">Если компонент работает только с другими компонентами платформа .NET Framework или не взаимодействует с другими компонентами, изменять ничего не нужно.</span><span class="sxs-lookup"><span data-stu-id="58882-117">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="58882-118">Если вы взаимодействуете с компонентом, не написанным для платформа .NET Framework, вы можете определить, поддерживает ли этот тип данных либо с помощью отражения, либо из документации.</span><span class="sxs-lookup"><span data-stu-id="58882-118">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="58882-119">Если это так, вам не нужно ничего менять.</span><span class="sxs-lookup"><span data-stu-id="58882-119">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="58882-120">При взаимоработе с компонентом, который не поддерживает этот тип данных, необходимо заменить его ближайшим CLS-совместимым типом.</span><span class="sxs-lookup"><span data-stu-id="58882-120">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="58882-121">Например, вместо `UInteger` вы можете использовать `Integer` , если вам не нужен диапазон значений, превышающий 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="58882-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="58882-122">Если вам нужен расширенный диапазон, вы можете заменить `UInteger` на `Long`.</span><span class="sxs-lookup"><span data-stu-id="58882-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="58882-123">При взаимоработе с автоматизацией или COM-объектами Помните, что некоторые типы имеют разную ширину данных, чем в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58882-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="58882-124">Например, данные типа `uint` часто являются 16-битными в других средах.</span><span class="sxs-lookup"><span data-stu-id="58882-124">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="58882-125">При передаче 16-разрядного аргумента в такой компонент объявите его как `UShort` вместо `UInteger` в управляемом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="58882-125">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="58882-126">См. также</span><span class="sxs-lookup"><span data-stu-id="58882-126">See also</span></span>

- <span data-ttu-id="58882-127">[Reflection (Visual Basic)](../../programming-guide/concepts/reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="58882-127">[Reflection (Visual Basic)](../../programming-guide/concepts/reflection.md)</span></span>
- [<span data-ttu-id="58882-128">Отражение</span><span class="sxs-lookup"><span data-stu-id="58882-128">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
