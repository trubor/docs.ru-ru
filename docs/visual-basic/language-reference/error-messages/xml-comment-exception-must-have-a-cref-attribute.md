---
description: 'Дополнительные сведения о: BC42319: Исключение комментария XML должно иметь атрибут cref'
title: Исключение комментария XML должно иметь атрибут cref
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: e602a2973d95f70d5ab532e6be319a9575d239a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701460"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="92901-103">BC42319: Исключение комментария XML должно иметь атрибут cref</span><span class="sxs-lookup"><span data-stu-id="92901-103">BC42319: XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="92901-104">\<exception>Тег предоставляет способ документирования исключений, которые могут быть вызваны методом.</span><span class="sxs-lookup"><span data-stu-id="92901-104">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="92901-105">Атрибут Required `cref` указывает имя члена, который проверяется генератором документации.</span><span class="sxs-lookup"><span data-stu-id="92901-105">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="92901-106">Если элемент существует, он преобразуется в каноническое имя элемента в файле документации.</span><span class="sxs-lookup"><span data-stu-id="92901-106">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="92901-107">**Идентификатор ошибки:** BC42319</span><span class="sxs-lookup"><span data-stu-id="92901-107">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="92901-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="92901-108">To correct this error</span></span>

<span data-ttu-id="92901-109">Добавьте `cref` атрибут к исключению следующим образом:</span><span class="sxs-lookup"><span data-stu-id="92901-109">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="92901-110">См. также</span><span class="sxs-lookup"><span data-stu-id="92901-110">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="92901-111">Практическое руководство. Создание XML-документации</span><span class="sxs-lookup"><span data-stu-id="92901-111">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="92901-112">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="92901-112">XML Comment Tags</span></span>](../xmldoc/index.md)
