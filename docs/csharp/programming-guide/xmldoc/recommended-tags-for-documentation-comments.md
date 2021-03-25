---
title: Руководство по программированию на C#. Рекомендуемые теги для комментариев документации
description: Сведения о рекомендуемых тегах для комментариев в документации. Просмотрите список рекомендуемых тегов и дополнительные ресурсы.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 74fd18a09458c399aa135552e5f6f0bca359f09e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477835"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="18e52-104">Руководство по программированию на C#. Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="18e52-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="18e52-105">Компилятор C# обрабатывает комментарии документации в коде и форматирует их в виде XML-файла, имя которого задается с помощью параметра командной строки **/doc**.</span><span class="sxs-lookup"><span data-stu-id="18e52-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="18e52-106">Для создания окончательной документации на основе сгенерированного компилятором файла можно создать пользовательское средство или применить такие средства, как [DocFX](https://dotnet.github.io/docfx/) или [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="18e52-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="18e52-107">Теги обрабатываются в конструкциях кода, таких как типы и члены типов.</span><span class="sxs-lookup"><span data-stu-id="18e52-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="18e52-108">Комментарии документации не применяются к пространству имен.</span><span class="sxs-lookup"><span data-stu-id="18e52-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="18e52-109">Компилятор обрабатывает любые теги, имеющие допустимый формат XML.</span><span class="sxs-lookup"><span data-stu-id="18e52-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="18e52-110">С помощью следующих тегов реализуются часто используемые в пользовательской документации возможности.</span><span class="sxs-lookup"><span data-stu-id="18e52-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="18e52-111">Tags</span><span class="sxs-lookup"><span data-stu-id="18e52-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="18e52-112">(\* указывает, что компилятор проверяет синтаксис.)</span><span class="sxs-lookup"><span data-stu-id="18e52-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="18e52-113">Чтобы ввести в текст комментария документации угловые скобки, используйте для символов `<` и `>` коды HTML `&lt;` и `&gt;` соответственно.</span><span class="sxs-lookup"><span data-stu-id="18e52-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="18e52-114">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="18e52-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="18e52-115">См. также</span><span class="sxs-lookup"><span data-stu-id="18e52-115">See also</span></span>

- [<span data-ttu-id="18e52-116">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="18e52-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="18e52-117">**DocumentationFile** (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="18e52-117">**DocumentationFile** (C# compiler options)</span></span>](../../language-reference/compiler-options/output.md#documentationfile)
- [<span data-ttu-id="18e52-118">Комментарии XML-документации</span><span class="sxs-lookup"><span data-stu-id="18e52-118">XML documentation comments</span></span>](./index.md)
