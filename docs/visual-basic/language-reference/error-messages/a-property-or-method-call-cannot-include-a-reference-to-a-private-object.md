---
description: 'Дополнительные сведения: вызов свойства или метода не может включать ссылку на закрытый объект либо как аргумент, либо как возвращаемое значение.'
title: Нельзя включить ссылку на закрытый объект при вызове свойства или функции в качестве аргумента или возвращаемого значения
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 8fe570c9ed789a5bac36aafa9b1ec2f507a55d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797202"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="e9133-103">Нельзя включить ссылку на закрытый объект при вызове свойства или функции в качестве аргумента или возвращаемого значения</span><span class="sxs-lookup"><span data-stu-id="e9133-103">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="e9133-104">Некоторые из возможных причин этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="e9133-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="e9133-105">клиент вызвал свойство или метод внепроцессного компонента и предпринял попытку передать ссылку на закрытый объект в качестве одного из аргументов;</span><span class="sxs-lookup"><span data-stu-id="e9133-105">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>

- <span data-ttu-id="e9133-106">внепроцессный компонент задействовал для клиента метод обратного вызова и предпринял попытку передать ссылку на закрытый объект;</span><span class="sxs-lookup"><span data-stu-id="e9133-106">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>

- <span data-ttu-id="e9133-107">внепроцессный компонент предпринял попытку передать ссылку на закрытый объект в качестве аргумента события, которые он вызывал;</span><span class="sxs-lookup"><span data-stu-id="e9133-107">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>

- <span data-ttu-id="e9133-108">клиент предпринял попытку назначить ссылку на закрытый объект для аргумента `ByRef` события, которое он обрабатывал.</span><span class="sxs-lookup"><span data-stu-id="e9133-108">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e9133-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e9133-109">To correct this error</span></span>

- <span data-ttu-id="e9133-110">Удаление ссылки.</span><span class="sxs-lookup"><span data-stu-id="e9133-110">Remove the reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9133-111">См. также</span><span class="sxs-lookup"><span data-stu-id="e9133-111">See also</span></span>

- [<span data-ttu-id="e9133-112">Частная</span><span class="sxs-lookup"><span data-stu-id="e9133-112">Private</span></span>](../modifiers/private.md)
