---
description: 'Дополнительные сведения: Документирование кода с помощью XML (Visual Basic)'
title: Документирование кода с помощью XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b554007bdd5183d0d92dc7ff62d08885f4b7f486
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476011"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="c5adf-103">Документирование кода с помощью XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5adf-103">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="c5adf-104">В Visual Basic можно документировать код с помощью XML.</span><span class="sxs-lookup"><span data-stu-id="c5adf-104">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="c5adf-105">Комментарии XML-документации</span><span class="sxs-lookup"><span data-stu-id="c5adf-105">XML documentation comments</span></span>

<span data-ttu-id="c5adf-106">Visual Basic предоставляет простой способ автоматического создания XML-документации для проектов.</span><span class="sxs-lookup"><span data-stu-id="c5adf-106">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="c5adf-107">Можно автоматически создать XML-схему для типов и членов, а затем предоставить сводные данные, описательную документацию для каждого параметра и другие замечания.</span><span class="sxs-lookup"><span data-stu-id="c5adf-107">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="c5adf-108">При соответствующей настройке XML-документация автоматически создается в XML-файл с тем же корневым именем файла, что и у проекта.</span><span class="sxs-lookup"><span data-stu-id="c5adf-108">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="c5adf-109">Дополнительные сведения см. в разделе [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-109">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="c5adf-110">XML-файл можно использовать или иным образом манипулировать как XML.</span><span class="sxs-lookup"><span data-stu-id="c5adf-110">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="c5adf-111">Этот файл находится в том же каталоге, что и файл Output. exe или. DLL проекта.</span><span class="sxs-lookup"><span data-stu-id="c5adf-111">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="c5adf-112">Документация XML начинается с `'''`.</span><span class="sxs-lookup"><span data-stu-id="c5adf-112">XML documentation starts with `'''`.</span></span> <span data-ttu-id="c5adf-113">Обработка этих комментариев имеет некоторые ограничения.</span><span class="sxs-lookup"><span data-stu-id="c5adf-113">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="c5adf-114">Документация должна представлять собой XML с правильным форматом.</span><span class="sxs-lookup"><span data-stu-id="c5adf-114">The documentation must be well-formed XML.</span></span> <span data-ttu-id="c5adf-115">Если XML сформирован неправильно, создается предупреждение, а файл документации содержит комментарий, в котором говорится, что обнаружена ошибка.</span><span class="sxs-lookup"><span data-stu-id="c5adf-115">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="c5adf-116">Разработчики могут создавать собственные наборы тегов.</span><span class="sxs-lookup"><span data-stu-id="c5adf-116">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="c5adf-117">Существует рекомендуемый набор тегов (см. раздел [теги комментариев XML](../../language-reference/xmldoc/index.md)).</span><span class="sxs-lookup"><span data-stu-id="c5adf-117">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="c5adf-118">Некоторые рекомендуемые теги имеют особые значения.</span><span class="sxs-lookup"><span data-stu-id="c5adf-118">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="c5adf-119">Тег \<param> используется для описания параметров.</span><span class="sxs-lookup"><span data-stu-id="c5adf-119">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="c5adf-120">При использовании этого тега компилятор проверяет, что параметр существует и все параметры описаны в документации.</span><span class="sxs-lookup"><span data-stu-id="c5adf-120">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="c5adf-121">При сбое проверки компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="c5adf-121">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="c5adf-122">Атрибут `cref` может быть присоединен к любому тегу для предоставления ссылки на элемент кода.</span><span class="sxs-lookup"><span data-stu-id="c5adf-122">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="c5adf-123">Компилятор проверяет наличие этого элемента кода.</span><span class="sxs-lookup"><span data-stu-id="c5adf-123">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="c5adf-124">При сбое проверки компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="c5adf-124">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="c5adf-125">Компилятор также учитывает любые `Imports` инструкции при поиске типа, описанного в `cref` атрибуте.</span><span class="sxs-lookup"><span data-stu-id="c5adf-125">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="c5adf-126">Этот \<summary> тег используется технологией IntelliSense в Visual Studio для отображения дополнительных сведений о типе или члене.</span><span class="sxs-lookup"><span data-stu-id="c5adf-126">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c5adf-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="c5adf-127">Related sections</span></span>

<span data-ttu-id="c5adf-128">Дополнительные сведения о создании XML-файла с комментариями к документации см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="c5adf-128">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="c5adf-129">-doc</span><span class="sxs-lookup"><span data-stu-id="c5adf-129">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="c5adf-130">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="c5adf-130">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="c5adf-131">Обработка XML-файла</span><span class="sxs-lookup"><span data-stu-id="c5adf-131">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="c5adf-132">Практическое руководство. Создание XML-документации</span><span class="sxs-lookup"><span data-stu-id="c5adf-132">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="c5adf-133">Средства XML в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5adf-133">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="c5adf-134">См. также</span><span class="sxs-lookup"><span data-stu-id="c5adf-134">See also</span></span>

- [<span data-ttu-id="c5adf-135">Разработка приложений в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5adf-135">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="c5adf-136">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5adf-136">Visual Basic Programming Guide</span></span>](../index.md)
