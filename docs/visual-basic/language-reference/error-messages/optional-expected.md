---
description: 'Дополнительные сведения о: BC30202: требуется "Optional"'
title: Ожидается Optional
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 543dbf6226d4d298d46764ee506b55e770c91604
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795551"
---
# <a name="bc30202-optional-expected"></a><span data-ttu-id="b4521-103">BC30202: требуется "Optional"</span><span class="sxs-lookup"><span data-stu-id="b4521-103">BC30202: 'Optional' expected</span></span>

<span data-ttu-id="b4521-104">За дополнительным аргументом в объявлении процедуры следует обязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="b4521-104">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="b4521-105">Каждый аргумент, следующий за необязательным аргументом, также должен быть необязательным.</span><span class="sxs-lookup"><span data-stu-id="b4521-105">Every argument following an optional argument must also be optional.</span></span>

 <span data-ttu-id="b4521-106">**Идентификатор ошибки:** BC30202</span><span class="sxs-lookup"><span data-stu-id="b4521-106">**Error ID:** BC30202</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b4521-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="b4521-107">To correct this error</span></span>

- <span data-ttu-id="b4521-108">Если аргумент должен быть обязательным, переместите его перед первым необязательным аргументом в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="b4521-108">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>

- <span data-ttu-id="b4521-109">Если аргумент должен быть необязательным, используйте `Optional` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="b4521-109">If the argument is intended to be optional, use the `Optional` keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4521-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b4521-110">See also</span></span>

- [<span data-ttu-id="b4521-111">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="b4521-111">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
