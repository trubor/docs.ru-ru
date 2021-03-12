---
title: Ошибки и предупреждения, касающиеся компилятора
description: Описания и решения для ошибок и предупреждений, выдаваемых компилятором F#.
ms.date: 12/21/2019
ms.openlocfilehash: 9769ddee989f0774cfae8842e60dbd3fd2065f9c
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190181"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="84b99-103">Сообщения компилятора F#</span><span class="sxs-lookup"><span data-stu-id="84b99-103">F# compiler messages</span></span>

<span data-ttu-id="84b99-104">В этом разделе подробно описаны ошибки и предупреждения, выдаваемые компилятором F# для определенных конструкций.</span><span class="sxs-lookup"><span data-stu-id="84b99-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="84b99-105">Наборы ошибок по умолчанию можно изменять следующими способами:</span><span class="sxs-lookup"><span data-stu-id="84b99-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="84b99-106">Рассмотрение определенных предупреждений в качестве ошибок с помощью параметра компилятора `-warnaserror+`.</span><span class="sxs-lookup"><span data-stu-id="84b99-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="84b99-107">Пропуск определенных предупреждений с помощью параметра компилятора `-nowarn`.</span><span class="sxs-lookup"><span data-stu-id="84b99-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="84b99-108">Если какое-то предупреждение или ошибка в этом разделе еще не записаны, сделайте что-то из следующего:</span><span class="sxs-lookup"><span data-stu-id="84b99-108">If a particular warning or error is not yet recorded in this section:</span></span>

- <span data-ttu-id="84b99-109">Перейдите в конец страницы и отправьте отзыв, включив в него номер или текст ошибки.</span><span class="sxs-lookup"><span data-stu-id="84b99-109">Go to the end of this page and send feedback that includes the number or text of the error, or</span></span>
- <span data-ttu-id="84b99-110">Добавьте их сами, выполнив инструкции из [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) и открыв запрос на вытягивание для данного репозитория.</span><span class="sxs-lookup"><span data-stu-id="84b99-110">Add it yourself by following the instructions in [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) and opening a pull request for this repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="84b99-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="84b99-111">See also</span></span>

- [<span data-ttu-id="84b99-112">Параметры компилятора F#</span><span class="sxs-lookup"><span data-stu-id="84b99-112">F# Compiler Options</span></span>](../compiler-options.md)
