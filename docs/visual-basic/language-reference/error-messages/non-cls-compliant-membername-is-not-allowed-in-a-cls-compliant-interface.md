---
description: 'Дополнительные сведения о: BC40033: не совместимо с CLS <membername> , не допускается в CLS-совместимом интерфейсе'
title: CLS-несовместимый <membername> не допускается в CLS-совместимом интерфейсе
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: 070b56a8bf9df930de5bb5e363a9b157fcdc7ad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795642"
---
# <a name="bc40033-non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="f8b94-103">BC40033: несовместимый с CLS \<membername> не допускается в CLS-совместимом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="f8b94-103">BC40033: Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>

<span data-ttu-id="f8b94-104">Свойство, процедура или событие в интерфейсе помечается так, как `<CLSCompliant(True)>` если бы сам интерфейс был помечен как `<CLSCompliant(False)>` или, не помечен.</span><span class="sxs-lookup"><span data-stu-id="f8b94-104">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>

 <span data-ttu-id="f8b94-105">Для интерфейса, совместимого со [независимостьм от языка и Language-Independent компонентами](../../../standard/language-independence-and-language-independent-components.md) (CLS), все его члены должны соответствовать требованиям.</span><span class="sxs-lookup"><span data-stu-id="f8b94-105">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>

 <span data-ttu-id="f8b94-106">При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость.</span><span class="sxs-lookup"><span data-stu-id="f8b94-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f8b94-107">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="f8b94-107">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="f8b94-108">Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.</span><span class="sxs-lookup"><span data-stu-id="f8b94-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="f8b94-109">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="f8b94-109">By default, this message is a warning.</span></span> <span data-ttu-id="f8b94-110">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f8b94-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="f8b94-111">**Идентификатор ошибки:** BC40033</span><span class="sxs-lookup"><span data-stu-id="f8b94-111">**Error ID:** BC40033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f8b94-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f8b94-112">To correct this error</span></span>

- <span data-ttu-id="f8b94-113">Если требуется обеспечить соответствие требованиям CLS и контролировать исходный код интерфейса, пометьте интерфейс как, `<CLSCompliant(True)>` Если все его члены соответствуют требованиям.</span><span class="sxs-lookup"><span data-stu-id="f8b94-113">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>

- <span data-ttu-id="f8b94-114">Если требуется CLS-совместимость и отсутствует контроль над исходным кодом интерфейса или если он не соответствует требованиям, определите этот член в другом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="f8b94-114">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>

- <span data-ttu-id="f8b94-115">Если требуется, чтобы этот член оставался в текущем интерфейсе, удалите <xref:System.CLSCompliantAttribute> из его определения или пометьте его как `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="f8b94-115">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8b94-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f8b94-116">See also</span></span>

- [<span data-ttu-id="f8b94-117">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="f8b94-117">Interface Statement</span></span>](../statements/interface-statement.md)
