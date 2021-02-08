---
description: 'Дополнительные сведения о: BC31122: Модификатор Custom недопустим для событий, объявленных без явных типов делегата'
title: Модификатор Custom недопустим для событий, объявленных без явных делегируемых типов
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 6cbddd31dfa9c923038f8ea706bfc49233574cfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796682"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="9d97b-103">BC31122: Модификатор Custom недопустим для событий, объявленных без явных типов делегата</span><span class="sxs-lookup"><span data-stu-id="9d97b-103">BC31122: 'Custom' modifier is not valid on events declared without explicit delegate types</span></span>

<span data-ttu-id="9d97b-104">В отличие от нестандартного события, `Custom Event` объявление требует наличия `As` предложения, следующего за именем события, которое явно указывает тип делегата для события.</span><span class="sxs-lookup"><span data-stu-id="9d97b-104">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>

 <span data-ttu-id="9d97b-105">Ненастраиваемые события могут быть определены с помощью предложения, `As` явного типа делегата или списка параметров, непосредственно следующего за именем события.</span><span class="sxs-lookup"><span data-stu-id="9d97b-105">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>

 <span data-ttu-id="9d97b-106">**Идентификатор ошибки:** BC31122</span><span class="sxs-lookup"><span data-stu-id="9d97b-106">**Error ID:** BC31122</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9d97b-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9d97b-107">To correct this error</span></span>

1. <span data-ttu-id="9d97b-108">Определите делегат с тем же списком параметров, что и пользовательское событие.</span><span class="sxs-lookup"><span data-stu-id="9d97b-108">Define a delegate with the same parameter list as the custom event.</span></span>

     <span data-ttu-id="9d97b-109">Например, если объект `Custom Event` был определен с помощью `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , соответствующий делегат будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9d97b-109">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. <span data-ttu-id="9d97b-110">Замените список параметров пользовательского события `As` предложением с указанием типа делегата.</span><span class="sxs-lookup"><span data-stu-id="9d97b-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>

     <span data-ttu-id="9d97b-111">Продолжая работу с примером, `Custom Event` объявление будет перезаписано следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9d97b-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a><span data-ttu-id="9d97b-112">Пример</span><span class="sxs-lookup"><span data-stu-id="9d97b-112">Example</span></span>

 <span data-ttu-id="9d97b-113">В этом примере объявляется `Custom Event` и указывается обязательное `As` предложение с типом делегата.</span><span class="sxs-lookup"><span data-stu-id="9d97b-113">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a><span data-ttu-id="9d97b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9d97b-114">See also</span></span>

- [<span data-ttu-id="9d97b-115">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="9d97b-115">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="9d97b-116">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="9d97b-116">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="9d97b-117">События</span><span class="sxs-lookup"><span data-stu-id="9d97b-117">Events</span></span>](../../programming-guide/language-features/events/index.md)
