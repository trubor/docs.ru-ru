---
description: 'Дополнительные сведения о: BC40031: имя несовместимо <membername> с CLS'
title: Имя <membername> не является CLS-совместимым
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 7abc4aee8bb468b523e5bdd2ac13947d19c926bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795759"
---
# <a name="bc40031-name-membername-is-not-cls-compliant"></a><span data-ttu-id="6dc25-103">BC40031: имя несовместимо \<membername> с CLS</span><span class="sxs-lookup"><span data-stu-id="6dc25-103">BC40031: Name \<membername> is not CLS-compliant</span></span>

<span data-ttu-id="6dc25-104">Сборка помечается как, `<CLSCompliant(True)>` но предоставляет член с именем, которое начинается с символа подчеркивания ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="6dc25-104">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>

 <span data-ttu-id="6dc25-105">Программный элемент может содержать один или несколько символов подчеркивания, но для соответствия [языковым независимостьм и Language-Independent компонентам](../../../standard/language-independence-and-language-independent-components.md) (CLS) он не должен начинаться с символа подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="6dc25-105">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="6dc25-106">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6dc25-106">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

 <span data-ttu-id="6dc25-107">При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость.</span><span class="sxs-lookup"><span data-stu-id="6dc25-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6dc25-108">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="6dc25-108">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="6dc25-109">Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.</span><span class="sxs-lookup"><span data-stu-id="6dc25-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="6dc25-110">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="6dc25-110">By default, this message is a warning.</span></span> <span data-ttu-id="6dc25-111">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6dc25-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="6dc25-112">**Идентификатор ошибки:** BC40031</span><span class="sxs-lookup"><span data-stu-id="6dc25-112">**Error ID:** BC40031</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6dc25-113">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6dc25-113">To correct this error</span></span>

- <span data-ttu-id="6dc25-114">Если вы управляете исходным кодом, измените его имя так, чтобы оно не начиналось с символа подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="6dc25-114">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>

- <span data-ttu-id="6dc25-115">Если требуется, чтобы имя элемента оставалось без изменений, удалите <xref:System.CLSCompliantAttribute> из его определения или пометьте как `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="6dc25-115">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="6dc25-116">Вы по-прежнему можете пометить сборку как `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="6dc25-116">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dc25-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6dc25-117">See also</span></span>

- [<span data-ttu-id="6dc25-118">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="6dc25-118">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="6dc25-119">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dc25-119">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
