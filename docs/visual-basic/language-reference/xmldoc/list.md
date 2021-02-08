---
description: Дополнительные сведения <list> (Visual Basic)
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: c9e2e8d1c370bfdeefae4a8f19b25acc6a336ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787439"
---
# <a name="list-visual-basic"></a><span data-ttu-id="05021-103">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05021-103">\<list> (Visual Basic)</span></span>

<span data-ttu-id="05021-104">Определяет список или таблицу.</span><span class="sxs-lookup"><span data-stu-id="05021-104">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05021-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="05021-105">Syntax</span></span>  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a><span data-ttu-id="05021-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="05021-106">Parameters</span></span>  

 `type`  
 <span data-ttu-id="05021-107">Тип списка.</span><span class="sxs-lookup"><span data-stu-id="05021-107">The type of the list.</span></span> <span data-ttu-id="05021-108">Должен быть "маркированным" для маркированного списка, "число" для нумерованного списка или "Таблица" для таблицы из двух столбцов.</span><span class="sxs-lookup"><span data-stu-id="05021-108">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="05021-109">Используется, только если `type` имеет значение "Table".</span><span class="sxs-lookup"><span data-stu-id="05021-109">Only used when `type` is "table."</span></span> <span data-ttu-id="05021-110">Термин для определения, который определен в теге description.</span><span class="sxs-lookup"><span data-stu-id="05021-110">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="05021-111">Если параметр `type` имеет значение "маркированный" или "Number", `description` то элемент списка, если `type` "Table", `description` является определением `term` .</span><span class="sxs-lookup"><span data-stu-id="05021-111">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05021-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="05021-112">Remarks</span></span>  

 <span data-ttu-id="05021-113">`<listheader>`Блок определяет заголовок таблицы или списка определений.</span><span class="sxs-lookup"><span data-stu-id="05021-113">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="05021-114">При определении таблицы необходимо указать `term` в заголовке только запись.</span><span class="sxs-lookup"><span data-stu-id="05021-114">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="05021-115">Каждый элемент в списке указывается в блоке `<item>`.</span><span class="sxs-lookup"><span data-stu-id="05021-115">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="05021-116">При создании списка определений необходимо указать `term` и `description` .</span><span class="sxs-lookup"><span data-stu-id="05021-116">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="05021-117">Однако для таблицы, маркированного списка или нумерованного списка необходимо указать только запись для `description` .</span><span class="sxs-lookup"><span data-stu-id="05021-117">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="05021-118">Число блоков `<item>` в списке или таблице не ограничено.</span><span class="sxs-lookup"><span data-stu-id="05021-118">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="05021-119">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="05021-119">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05021-120">Пример</span><span class="sxs-lookup"><span data-stu-id="05021-120">Example</span></span>  

 <span data-ttu-id="05021-121">В этом примере `<list>` тег используется для определения маркированного списка в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="05021-121">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="05021-122">См. также</span><span class="sxs-lookup"><span data-stu-id="05021-122">See also</span></span>

- [<span data-ttu-id="05021-123">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="05021-123">XML Comment Tags</span></span>](index.md)
