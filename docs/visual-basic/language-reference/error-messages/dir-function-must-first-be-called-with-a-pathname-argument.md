---
description: Дополнительные сведения о функции "Dir" должны быть вызваны с аргументом "PathName".
title: Функция Dir должна первый раз вызываться с аргументом PathName
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: ee492a269d41e8c9fe1fddbd59210b59fbe8618c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796591"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="ca7c5-103">Функция Dir должна первый раз вызываться с аргументом PathName</span><span class="sxs-lookup"><span data-stu-id="ca7c5-103">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="ca7c5-104">Начальный вызов `Dir` функции не включает `PathName` аргумент.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-104">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="ca7c5-105">Первый вызов `Dir` должен включать `PathName` , но последующие вызовы `Dir` не обязательно должны включать параметры для получения следующего элемента.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-105">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ca7c5-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ca7c5-106">To correct this error</span></span>

- <span data-ttu-id="ca7c5-107">Укажите `PathName` аргумент в вызове функции.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-107">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca7c5-108">См. также</span><span class="sxs-lookup"><span data-stu-id="ca7c5-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
