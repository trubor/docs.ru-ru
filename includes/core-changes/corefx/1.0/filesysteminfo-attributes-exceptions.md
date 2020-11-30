---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032080"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="19d87-101">Исключение UnauthorizedAccessException, вызванное FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="19d87-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="19d87-102">В .NET Core <xref:System.UnauthorizedAccessException> возникает, когда вызывающий пытается задать значение атрибута файла, но у него нет разрешений на запись.</span><span class="sxs-lookup"><span data-stu-id="19d87-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="19d87-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="19d87-103">Change description</span></span>

<span data-ttu-id="19d87-104">В .NET Framework <xref:System.ArgumentException> возникает, когда вызывающий пытается задать значение атрибута файла в <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, но у него нет разрешений на запись.</span><span class="sxs-lookup"><span data-stu-id="19d87-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="19d87-105">В .NET Core вместо него возникает <xref:System.UnauthorizedAccessException></span><span class="sxs-lookup"><span data-stu-id="19d87-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="19d87-106">(в .NET Core <xref:System.ArgumentException> по-прежнему возникает, если вызывающий пытается задать недопустимый атрибут файла).</span><span class="sxs-lookup"><span data-stu-id="19d87-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19d87-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="19d87-107">Version introduced</span></span>

<span data-ttu-id="19d87-108">1.0</span><span class="sxs-lookup"><span data-stu-id="19d87-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19d87-109">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="19d87-109">Recommended action</span></span>

<span data-ttu-id="19d87-110">Изменяйте любые инструкции `catch`, чтобы получить <xref:System.UnauthorizedAccessException> вместо или в дополнение к <xref:System.ArgumentException> по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="19d87-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="19d87-111">Категория</span><span class="sxs-lookup"><span data-stu-id="19d87-111">Category</span></span>

<span data-ttu-id="19d87-112">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="19d87-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19d87-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="19d87-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
