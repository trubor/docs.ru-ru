---
description: Дополнительные сведения см. в статье Устранение неполадок наследуемых обработчиков событий в Visual Basic
title: Устранение неполадок, связанных с унаследованными обработчиками событий
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: b489b6c85510bb942b403a508b6bbe232c3e1853
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424480"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="287ad-103">Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="287ad-103">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>

<span data-ttu-id="287ad-104">В этом разделе перечислены распространенные проблемы, возникающие при работе с обработчиками событий в наследуемых компонентах.</span><span class="sxs-lookup"><span data-stu-id="287ad-104">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="287ad-105">Процедуры</span><span class="sxs-lookup"><span data-stu-id="287ad-105">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="287ad-106">Код в обработчике событий выполняется дважды для каждого вызова</span><span class="sxs-lookup"><span data-stu-id="287ad-106">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="287ad-107">Наследуемый обработчик событий не должен включать предложение [Handles](../../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="287ad-107">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="287ad-108">Метод в базовом классе уже связан с событием и будет срабатывать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="287ad-108">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="287ad-109">Удалите `Handles` предложение из унаследованного метода.</span><span class="sxs-lookup"><span data-stu-id="287ad-109">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="287ad-110">Если наследуемый метод не имеет `Handles` ключевого слова, убедитесь, что код не содержит лишних [операторов AddHandler](../../../language-reference/statements/addhandler-statement.md) или дополнительных методов, обрабатывающих это же событие.</span><span class="sxs-lookup"><span data-stu-id="287ad-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="287ad-111">См. также</span><span class="sxs-lookup"><span data-stu-id="287ad-111">See also</span></span>

- [<span data-ttu-id="287ad-112">События</span><span class="sxs-lookup"><span data-stu-id="287ad-112">Events</span></span>](index.md)
