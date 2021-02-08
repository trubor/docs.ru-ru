---
description: 'Дополнительные сведения о: BC40008: " <elementname> " является устаревшим (Visual Basic Warning)'
title: <elementname> является устаревшим (Предупреждение Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 6fea3526f19b139af103f21ddd89f2272eb6eac5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796578"
---
# <a name="bc40008-elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="c6d8b-103">BC40008: " \<elementname> " является устаревшим (Visual Basic Warning)</span><span class="sxs-lookup"><span data-stu-id="c6d8b-103">BC40008: '\<elementname>' is obsolete (Visual Basic Warning)</span></span>

<span data-ttu-id="c6d8b-104">Оператор пытается получить доступ к элементу программирования, который был помечен атрибутом <xref:System.ObsoleteAttribute> и директивой, предписывающей расценивать это как предупреждение.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-104">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>

 <span data-ttu-id="c6d8b-105">Вы можете пометить любой программный элемент как неиспользуемый, применив к нему атрибут <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c6d8b-105">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="c6d8b-106">Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-106">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="c6d8b-107">Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-107">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="c6d8b-108">Если задать значение `False`или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-108">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>

 <span data-ttu-id="c6d8b-109">По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-109">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="c6d8b-110">Дополнительные сведения о сокрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c6d8b-110">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c6d8b-111">**Идентификатор ошибки:** BC40008</span><span class="sxs-lookup"><span data-stu-id="c6d8b-111">**Error ID:** BC40008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c6d8b-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c6d8b-112">To correct this error</span></span>

- <span data-ttu-id="c6d8b-113">Убедитесь, что в ссылке исходного кода имя элемента указано правильно.</span><span class="sxs-lookup"><span data-stu-id="c6d8b-113">Ensure that the source-code reference is spelling the element name correctly.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6d8b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c6d8b-114">See also</span></span>

- [<span data-ttu-id="c6d8b-115">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="c6d8b-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
