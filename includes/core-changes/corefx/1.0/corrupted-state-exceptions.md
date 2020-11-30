---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032066"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="0cc47-101">Обработка исключений поврежденного состояния не поддерживается</span><span class="sxs-lookup"><span data-stu-id="0cc47-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="0cc47-102">Обработка исключений поврежденного состояния в .NET Core не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="0cc47-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0cc47-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0cc47-103">Change description</span></span>

<span data-ttu-id="0cc47-104">Ранее исключения поврежденного состояния процесса могли быть перехвачены и обработаны обработчиками исключений управляемого кода, например с помощью инструкции [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) в C#.</span><span class="sxs-lookup"><span data-stu-id="0cc47-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="0cc47-105">Начиная с .NET Core 1.0 исключения поврежденного состояния процесса не могут обрабатываться управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="0cc47-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="0cc47-106">Среда CLR не доставляет исключения поврежденного состояния процесса в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="0cc47-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0cc47-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0cc47-107">Version introduced</span></span>

<span data-ttu-id="0cc47-108">1.0</span><span class="sxs-lookup"><span data-stu-id="0cc47-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0cc47-109">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0cc47-109">Recommended action</span></span>

<span data-ttu-id="0cc47-110">Старайтесь исключить потребность в обработке исключений поврежденного состояния процесса, устраняя ситуации, которые вызывают подобные исключения.</span><span class="sxs-lookup"><span data-stu-id="0cc47-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="0cc47-111">Если обработка исключений поврежденного состояния процесса совершенно необходима, напишите обработчик исключений в коде C или C++.</span><span class="sxs-lookup"><span data-stu-id="0cc47-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="0cc47-112">Категория</span><span class="sxs-lookup"><span data-stu-id="0cc47-112">Category</span></span>

<span data-ttu-id="0cc47-113">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="0cc47-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0cc47-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0cc47-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="0cc47-115">Элемент legacyCorruptedStateExceptionsPolicy</span><span class="sxs-lookup"><span data-stu-id="0cc47-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
