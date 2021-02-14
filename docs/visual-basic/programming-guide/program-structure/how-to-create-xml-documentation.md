---
description: Дополнительные сведения см. в статье Создание документации по XML в Visual Basic
title: Практическое руководство. Создание XML-документации
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d54c79d820a170b246e5c85d7562487fbe66f39c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475959"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="2729a-103">Практическое руководство. Создание XML-документации в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2729a-103">How to: Create XML Documentation in Visual Basic</span></span>

<span data-ttu-id="2729a-104">В этом примере показано, как добавить комментарии XML-документации в код.</span><span class="sxs-lookup"><span data-stu-id="2729a-104">This example shows how to add XML documentation comments to your code.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="2729a-105">Создание XML-документации для типа или члена</span><span class="sxs-lookup"><span data-stu-id="2729a-105">To create XML documentation for a type or member</span></span>

1. <span data-ttu-id="2729a-106">В **редакторе кода** поместите курсор в строку над типом или членом, для которого требуется создать документацию.</span><span class="sxs-lookup"><span data-stu-id="2729a-106">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>

2. <span data-ttu-id="2729a-107">Тип `'''` (три одинарные кавычки).</span><span class="sxs-lookup"><span data-stu-id="2729a-107">Type `'''` (three single-quotation marks).</span></span>

    <span data-ttu-id="2729a-108">В **редакторе кода** ДОБАВЛЯЕТСЯ XML-схема для типа или члена.</span><span class="sxs-lookup"><span data-stu-id="2729a-108">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>

3. <span data-ttu-id="2729a-109">Добавьте описательные сведения между соответствующими тегами.</span><span class="sxs-lookup"><span data-stu-id="2729a-109">Add descriptive information between the appropriate tags.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2729a-110">При добавлении дополнительных строк в блок XML-документации каждая строка должна начинаться с `'''` .</span><span class="sxs-lookup"><span data-stu-id="2729a-110">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>

4. <span data-ttu-id="2729a-111">Добавьте дополнительный код, который использует тип или член с новыми комментариями XML-документации.</span><span class="sxs-lookup"><span data-stu-id="2729a-111">Add additional code that uses the type or member with the new XML documentation comments.</span></span>

    <span data-ttu-id="2729a-112">IntelliSense отображает текст из \<summary> тега для типа или члена.</span><span class="sxs-lookup"><span data-stu-id="2729a-112">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>

5. <span data-ttu-id="2729a-113">Скомпилируйте код, чтобы создать XML-файл, содержащий комментарии к документации.</span><span class="sxs-lookup"><span data-stu-id="2729a-113">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="2729a-114">Дополнительные сведения см. в разделе [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="2729a-114">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2729a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="2729a-115">See also</span></span>

- [<span data-ttu-id="2729a-116">Документирование кода с помощью XML</span><span class="sxs-lookup"><span data-stu-id="2729a-116">Documenting Your Code with XML</span></span>](documenting-your-code-with-xml.md)
- [<span data-ttu-id="2729a-117">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="2729a-117">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="2729a-118">-doc</span><span class="sxs-lookup"><span data-stu-id="2729a-118">-doc</span></span>](../../reference/command-line-compiler/doc.md)
