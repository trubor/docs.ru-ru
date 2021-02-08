---
description: 'Дополнительные сведения: <code>(Visual Basic)'
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 80fc0988f60d9d82b9c88734f86b20ebccc80b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787504"
---
# <a name="code-visual-basic"></a><span data-ttu-id="3089c-102">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3089c-102">\<code> (Visual Basic)</span></span>

<span data-ttu-id="3089c-103">Указывает, что текст представляет собой несколько строк кода.</span><span class="sxs-lookup"><span data-stu-id="3089c-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3089c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3089c-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3089c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3089c-105">Parameters</span></span>  

 `content`  
 <span data-ttu-id="3089c-106">Текст, помечающий как код.</span><span class="sxs-lookup"><span data-stu-id="3089c-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3089c-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="3089c-107">Remarks</span></span>  

 <span data-ttu-id="3089c-108">Используйте `<code>` тег, чтобы указать несколько строк в виде кода.</span><span class="sxs-lookup"><span data-stu-id="3089c-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="3089c-109">Используйте, [\<c>](c.md) чтобы указать, что текст в описании должен быть помечен как код.</span><span class="sxs-lookup"><span data-stu-id="3089c-109">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="3089c-110">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="3089c-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3089c-111">Пример</span><span class="sxs-lookup"><span data-stu-id="3089c-111">Example</span></span>  

 <span data-ttu-id="3089c-112">В этом примере \<code> тег используется для включения примера кода для использования `ID` поля.</span><span class="sxs-lookup"><span data-stu-id="3089c-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3089c-113">См. также</span><span class="sxs-lookup"><span data-stu-id="3089c-113">See also</span></span>

- [<span data-ttu-id="3089c-114">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="3089c-114">XML Comment Tags</span></span>](index.md)
