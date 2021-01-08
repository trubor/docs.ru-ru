---
title: Ошибки и предупреждения, касающиеся компилятора
description: Описания и решения для ошибок и предупреждений, выдаваемых компилятором F#.
ms.date: 12/21/2019
ms.openlocfilehash: 58430297abe807027afdc52841d67d1233401ff1
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856124"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="46132-103">Сообщения компилятора F#</span><span class="sxs-lookup"><span data-stu-id="46132-103">F# compiler messages</span></span>

<span data-ttu-id="46132-104">В этом разделе подробно описаны ошибки и предупреждения, выдаваемые компилятором F# для определенных конструкций.</span><span class="sxs-lookup"><span data-stu-id="46132-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="46132-105">Наборы ошибок по умолчанию можно изменять следующими способами:</span><span class="sxs-lookup"><span data-stu-id="46132-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="46132-106">Рассмотрение определенных предупреждений в качестве ошибок с помощью параметра компилятора `-warnaserror+`.</span><span class="sxs-lookup"><span data-stu-id="46132-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="46132-107">Пропуск определенных предупреждений с помощью параметра компилятора `-nowarn`.</span><span class="sxs-lookup"><span data-stu-id="46132-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="46132-108">Если какое-то предупреждение или ошибка в этом разделе еще не записаны, сделайте что-то из следующего:</span><span class="sxs-lookup"><span data-stu-id="46132-108">If a particular warning or error is not yet recorded in this section:</span></span>

- <span data-ttu-id="46132-109">Перейдите в конец страницы и отправьте отзыв, включив в него номер или текст ошибки.</span><span class="sxs-lookup"><span data-stu-id="46132-109">Go to the end of this page and send feedback that includes the number or text of the error, or</span></span>
- <span data-ttu-id="46132-110">Добавьте их сами, выполнив инструкции из [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/master/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) и открыв запрос на вытягивание для данного репозитория.</span><span class="sxs-lookup"><span data-stu-id="46132-110">Add it yourself by following the instructions in [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/master/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) and opening a pull request for this repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="46132-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="46132-111">See also</span></span>

- [<span data-ttu-id="46132-112">Параметры компилятора F#</span><span class="sxs-lookup"><span data-stu-id="46132-112">F# Compiler Options</span></span>](../compiler-options.md)
