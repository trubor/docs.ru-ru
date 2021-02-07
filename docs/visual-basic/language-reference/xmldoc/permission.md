---
description: Дополнительные сведения <permission> (Visual Basic)
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7a227e97051002c834c96297d3028f08e3ed07ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700264"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="f3e78-103">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3e78-103">\<permission> (Visual Basic)</span></span>

<span data-ttu-id="f3e78-104">Указывает требуемое разрешение для элемента.</span><span class="sxs-lookup"><span data-stu-id="f3e78-104">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3e78-105">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e78-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f3e78-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="f3e78-107">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="f3e78-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f3e78-108">Компилятор проверяет, существует ли элемент кода, и приводит `member` к каноническому имени элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="f3e78-108">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="f3e78-109">Заключите `member` в кавычки ("").</span><span class="sxs-lookup"><span data-stu-id="f3e78-109">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="f3e78-110">Описание уровня доступа для члена.</span><span class="sxs-lookup"><span data-stu-id="f3e78-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e78-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="f3e78-111">Remarks</span></span>  

 <span data-ttu-id="f3e78-112">Используйте `<permission>` тег для документирования доступа к элементу.</span><span class="sxs-lookup"><span data-stu-id="f3e78-112">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="f3e78-113">Используйте <xref:System.Security.PermissionSet> класс, чтобы указать доступ к элементу.</span><span class="sxs-lookup"><span data-stu-id="f3e78-113">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="f3e78-114">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="f3e78-114">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e78-115">Пример</span><span class="sxs-lookup"><span data-stu-id="f3e78-115">Example</span></span>  

 <span data-ttu-id="f3e78-116">В этом примере `<permission>` тег используется для описания того, что объект <xref:System.Security.Permissions.FileIOPermission> является обязательным для `ReadFile` метода.</span><span class="sxs-lookup"><span data-stu-id="f3e78-116">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e78-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f3e78-117">See also</span></span>

- [<span data-ttu-id="f3e78-118">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="f3e78-118">XML Comment Tags</span></span>](index.md)
