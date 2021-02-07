---
description: Дополнительные сведения <para> (Visual Basic)
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 51dd9ff300d980b4c0576566cad5d17375889ba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740773"
---
# <a name="para-visual-basic"></a><span data-ttu-id="5cd60-103">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cd60-103">\<para> (Visual Basic)</span></span>

<span data-ttu-id="5cd60-104">Указывает, что содержимое форматируется как абзац.</span><span class="sxs-lookup"><span data-stu-id="5cd60-104">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd60-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cd60-105">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd60-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5cd60-106">Parameters</span></span>  

 `content`  
 <span data-ttu-id="5cd60-107">Текст абзаца.</span><span class="sxs-lookup"><span data-stu-id="5cd60-107">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cd60-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="5cd60-108">Remarks</span></span>  

 <span data-ttu-id="5cd60-109">Тег `<para>` используется внутри другого тега, например [\<summary>](summary.md), [\<remarks>](remarks.md) или [\<returns>](returns.md), и позволяет добавить к тексту структуру.</span><span class="sxs-lookup"><span data-stu-id="5cd60-109">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="5cd60-110">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="5cd60-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd60-111">Пример</span><span class="sxs-lookup"><span data-stu-id="5cd60-111">Example</span></span>  

 <span data-ttu-id="5cd60-112">В этом примере `<para>` тег используется для разбиения раздела примечаний для `UpdateRecord` метода на два абзаца.</span><span class="sxs-lookup"><span data-stu-id="5cd60-112">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5cd60-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5cd60-113">See also</span></span>

- [<span data-ttu-id="5cd60-114">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="5cd60-114">XML Comment Tags</span></span>](index.md)
