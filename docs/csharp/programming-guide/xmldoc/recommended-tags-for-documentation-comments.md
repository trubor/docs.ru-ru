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
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Руководство по программированию на C#. Рекомендуемые теги для комментариев документации

Компилятор C# обрабатывает комментарии документации в коде и форматирует их в виде XML-файла, имя которого задается с помощью параметра командной строки **/doc**. Для создания окончательной документации на основе сгенерированного компилятором файла можно создать пользовательское средство или применить такие средства, как [DocFX](https://dotnet.github.io/docfx/) или [Sandcastle](https://github.com/EWSoftware/SHFB).

Теги обрабатываются в конструкциях кода, таких как типы и члены типов.

> [!NOTE]
> Комментарии документации не применяются к пространству имен.  
  
 Компилятор обрабатывает любые теги, имеющие допустимый формат XML. С помощью следующих тегов реализуются часто используемые в пользовательской документации возможности.  
  
## <a name="tags"></a>Tags  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* указывает, что компилятор проверяет синтаксис.)

Чтобы ввести в текст комментария документации угловые скобки, используйте для символов `<` и `>` коды HTML `&lt;` и `&gt;` соответственно. Это показано в следующем примере.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [**DocumentationFile** (параметры компилятора C#)](../../language-reference/compiler-options/output.md#documentationfile)
- [Комментарии XML-документации](./index.md)
