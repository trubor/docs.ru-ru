---
title: Руководство по программированию на C#. <c>
description: Сведения о теге <c> в XML. С помощью этого тега можно пометить однострочный текст в описании как код, если код <code> представлен несколькими строкамиindicates multiple lines..
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: fc445c7245287c3835543e4bbe4b3b46ec46fd35
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478697"
---
# <a name="c-c-programming-guide"></a>\<c> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<c>text</c>
```

## <a name="parameters"></a>Параметры

- `text`

  Текст, который нужно указать в качестве кода.

## <a name="remarks"></a>Примечания

С помощью тега `<c>` можно указать, что текст в описании необходимо пометить как код. Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](./code.md).

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
