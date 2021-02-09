---
description: 'Узнайте подробнее о: <inheritdoc> (руководство по программированию на C#)'
title: <inheritdoc> — руководство по программированию на C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 960bdfbcec1e3f6a89675273f63b6d398e44947e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719400"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="2a7da-103">\<inheritdoc> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="2a7da-103">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a7da-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2a7da-104">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="2a7da-105">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="2a7da-105">InheritDoc</span></span>

<span data-ttu-id="2a7da-106">Наследование XML-комментариев от базовых классов, интерфейсов и аналогичных методов.</span><span class="sxs-lookup"><span data-stu-id="2a7da-106">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="2a7da-107">Это позволяет обойтись без копирования и вставки одинаковых XML-комментариев и автоматически поддерживать их синхронизацию.</span><span class="sxs-lookup"><span data-stu-id="2a7da-107">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2a7da-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="2a7da-108">Remarks</span></span>  

<span data-ttu-id="2a7da-109">Добавьте XML-комментарии в базовые классы или интерфейсы, и InheritDoc скопирует их во все реализации классов.</span><span class="sxs-lookup"><span data-stu-id="2a7da-109">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="2a7da-110">Добавьте XML-комментарии в синхронные методы, и InheritDoc скопирует их в асинхронные версии аналогичных методов.</span><span class="sxs-lookup"><span data-stu-id="2a7da-110">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="2a7da-111">Если вам нужно скопировать комментарии из определенного элемента, укажите нужный элемент в атрибуте `cref`.</span><span class="sxs-lookup"><span data-stu-id="2a7da-111">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="2a7da-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="2a7da-112">Examples</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="2a7da-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2a7da-113">See also</span></span>

- [<span data-ttu-id="2a7da-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="2a7da-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2a7da-115">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="2a7da-115">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
