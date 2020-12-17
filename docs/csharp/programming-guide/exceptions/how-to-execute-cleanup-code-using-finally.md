---
title: Руководство по программированию на C#. Выполнение кода очистки с использованием блока finally
description: Сведения о выполнении кода очистки с использованием оператора finally. Операторы finally гарантируют, что все необходимые очистки объектов происходят немедленно.
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110186"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="13190-104">Руководство по программированию на C#. Выполнение кода очистки с использованием блока finally</span><span class="sxs-lookup"><span data-stu-id="13190-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="13190-105">Оператор `finally` позволяет гарантировать, что необходимая очистка объектов, как правило, объектов, занимающих внешние ресурсы, возникает немедленно, даже при создании исключения.</span><span class="sxs-lookup"><span data-stu-id="13190-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="13190-106">Примером подобной очистки является вызов <xref:System.IO.Stream.Close%2A> для <xref:System.IO.FileStream> сразу после использования вместо ожидания сборки мусора, выполняемой для объекта средой CLR, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="13190-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a><span data-ttu-id="13190-107">Пример</span><span class="sxs-lookup"><span data-stu-id="13190-107">Example</span></span>

<span data-ttu-id="13190-108">Чтобы преобразовать предыдущий код в оператор `try-catch-finally`, код очистки отделяется от рабочего кода следующим образом:</span><span class="sxs-lookup"><span data-stu-id="13190-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

<span data-ttu-id="13190-109">Так как исключение в блоке `try` может возникнуть в любой момент до вызова `OpenWrite()` или может произойти сбой самого вызова `OpenWrite()`, мы не можем гарантировать, что файл, который мы попытаемся закрыть, будет в это время открыт.</span><span class="sxs-lookup"><span data-stu-id="13190-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we aren't guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="13190-110">Блок `finally` добавляет проверку того, что объект <xref:System.IO.FileStream> — не `null`, перед вызовом метода <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="13190-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object isn't `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="13190-111">Без проверки `null` блок `finally` может вызывать собственное исключение <xref:System.NullReferenceException>, однако вызова исключений в блоках `finally` следует по возможности избегать.</span><span class="sxs-lookup"><span data-stu-id="13190-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it's possible.</span></span>

<span data-ttu-id="13190-112">Подключение к базе данных — еще один подходящий кандидат для заключения в блок `finally`.</span><span class="sxs-lookup"><span data-stu-id="13190-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="13190-113">Так как количество разрешенных подключений к серверу базы данных иногда ограничено, закрывать подключения к базе данных рекомендуется как можно быстрее.</span><span class="sxs-lookup"><span data-stu-id="13190-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="13190-114">Если перед закрытием подключения возникает исключение, рекомендуется использовать блок `finally`, а не ожидать сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="13190-114">If an exception is thrown before you can close your connection, using the `finally` block is better than waiting for garbage collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="13190-115">См. также</span><span class="sxs-lookup"><span data-stu-id="13190-115">See also</span></span>

- [<span data-ttu-id="13190-116">Оператор using</span><span class="sxs-lookup"><span data-stu-id="13190-116">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="13190-117">try-catch</span><span class="sxs-lookup"><span data-stu-id="13190-117">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="13190-118">try-finally</span><span class="sxs-lookup"><span data-stu-id="13190-118">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="13190-119">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="13190-119">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
