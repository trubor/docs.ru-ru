---
description: 'Дополнительные сведения о: мышь отсутствует'
title: Не обнаружена мышь.
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 1964f1def655a1e38ce2b8919a69ab2e6ac929a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479131"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="4cc8d-103">Не обнаружена мышь.</span><span class="sxs-lookup"><span data-stu-id="4cc8d-103">No mouse is present</span></span>

<span data-ttu-id="4cc8d-104">Было вызвано одно из свойств объекта `My.Computer.Mouse` , но на компьютере отсутствует установленная мышь или порт мыши.</span><span class="sxs-lookup"><span data-stu-id="4cc8d-104">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cc8d-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="4cc8d-105">To correct this error</span></span>  
  
- <span data-ttu-id="4cc8d-106">Добавьте блок `Try...Catch` вокруг вызова свойства объекта `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="4cc8d-106">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="4cc8d-107">Или...</span><span class="sxs-lookup"><span data-stu-id="4cc8d-107">— or —</span></span>  
  
- <span data-ttu-id="4cc8d-108">Установите мышь на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4cc8d-108">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc8d-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4cc8d-109">See also</span></span>

- [<span data-ttu-id="4cc8d-110">My.Computer.Mouse</span><span class="sxs-lookup"><span data-stu-id="4cc8d-110">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="4cc8d-111">Обработка и создание исключений в .NET</span><span class="sxs-lookup"><span data-stu-id="4cc8d-111">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="4cc8d-112">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="4cc8d-112">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
