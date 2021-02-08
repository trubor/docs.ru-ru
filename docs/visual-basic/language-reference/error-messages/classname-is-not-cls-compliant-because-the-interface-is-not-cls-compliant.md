---
description: 'Дополнительные сведения о: BC40029: " <classname> " несовместим с CLS, поскольку интерфейс "", который <interfacename> он реализует, НЕСОВМЕСТИМ с CLS'
title: <classname> несовместимо с CLS, так как интерфейс <interfacename>, который он реализует, несовместим с CLS
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 28264dd602bd20a6b33bebd965982ca12d402d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796774"
---
# <a name="bc40029-classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="caf03-103">BC40029: " \<classname> " несовместим с CLS, поскольку интерфейс "", который \<interfacename> он реализует, НЕСОВМЕСТИМ с CLS</span><span class="sxs-lookup"><span data-stu-id="caf03-103">BC40029: '\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>

<span data-ttu-id="caf03-104">Класс или интерфейс помечен как `<CLSCompliant(True)>` , если он наследует или реализует тип, помеченный как `<CLSCompliant(False)>` или не помеченный совсем.</span><span class="sxs-lookup"><span data-stu-id="caf03-104">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>

 <span data-ttu-id="caf03-105">Чтобы класс или интерфейс соответствовал требованиям [независимости от языка и Language-Independent компонентов](../../../standard/language-independence-and-language-independent-components.md) (CLS), его полная иерархия наследования должна соответствовать требованиям.</span><span class="sxs-lookup"><span data-stu-id="caf03-105">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="caf03-106">Это означает, что каждый тип, от которого он наследуется прямо или косвенно, должен быть соответствующим.</span><span class="sxs-lookup"><span data-stu-id="caf03-106">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="caf03-107">Аналогично, если класс реализует один или несколько интерфейсов, то все они должны быть совместимыми по всей иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="caf03-107">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>

 <span data-ttu-id="caf03-108">При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость.</span><span class="sxs-lookup"><span data-stu-id="caf03-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="caf03-109">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="caf03-109">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="caf03-110">Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.</span><span class="sxs-lookup"><span data-stu-id="caf03-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="caf03-111">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="caf03-111">By default, this message is a warning.</span></span> <span data-ttu-id="caf03-112">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="caf03-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="caf03-113">**Идентификатор ошибки:** BC40029</span><span class="sxs-lookup"><span data-stu-id="caf03-113">**Error ID:** BC40029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="caf03-114">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="caf03-114">To correct this error</span></span>

- <span data-ttu-id="caf03-115">Если требуется совместимость с CLS, определите этот тип в другой иерархии наследования или схеме реализации.</span><span class="sxs-lookup"><span data-stu-id="caf03-115">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>

- <span data-ttu-id="caf03-116">Если требуется, чтобы этот тип оставался в текущей иерархии наследования или схеме реализации, удалите <xref:System.CLSCompliantAttribute> из его определения или пометьте его как `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="caf03-116">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>
