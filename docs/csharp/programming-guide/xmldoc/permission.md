---
title: <permission> Руководство по программированию на C#.
description: Сведения о теге <permission> XML. Этот тег позволяет документировать доступ члена, а класс PermissionSet позволяет определить доступ к члену.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 379d3fda06c50e9e988784e671061d604e6e5b36
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477849"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="743eb-105">\<permission> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="743eb-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="743eb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="743eb-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="743eb-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="743eb-107">Parameters</span></span>

- <span data-ttu-id="743eb-108">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="743eb-108">cref = " `member`"</span></span>

  <span data-ttu-id="743eb-109">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="743eb-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="743eb-110">Компилятор проверяет, существует ли элемент кода, и приводит `member` к каноническому имени элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="743eb-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="743eb-111">*member* необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="743eb-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="743eb-112">Сведения о создании ссылки cref на универсальный тип см. в статье об [атрибуте cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="743eb-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="743eb-113">Описание уровня доступа для члена.</span><span class="sxs-lookup"><span data-stu-id="743eb-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="743eb-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="743eb-114">Remarks</span></span>

<span data-ttu-id="743eb-115">Тег `<permission>` позволяет документировать уровень доступа для элемента.</span><span class="sxs-lookup"><span data-stu-id="743eb-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="743eb-116">Задать уровень доступа для члена можно с помощью класса <xref:System.Security.PermissionSet>.</span><span class="sxs-lookup"><span data-stu-id="743eb-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="743eb-117">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="743eb-117">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="743eb-118">Пример</span><span class="sxs-lookup"><span data-stu-id="743eb-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="743eb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="743eb-119">See also</span></span>

- [<span data-ttu-id="743eb-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="743eb-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="743eb-121">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="743eb-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
