---
title: Руководство по программированию на C#. <paramref>
description: Сведения о теге <paramref> в XML. Этот тег позволяет указать, что присутствующее в коде слово является параметром.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e559a899aad7806bb7ccef32be49954fabed6a32
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477871"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра, на который указывается ссылка. Имя заключается в двойные кавычки (" ").

## <a name="remarks"></a>Примечания

Тег `<paramref>` позволяет указать, что слово в комментариях к коду, например в блоке `<summary>` или `<remarks>`, ссылается на параметр. В XML-файл такое слово может выделяться особым образом, например курсивом или полужирным шрифтом.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>См. также раздел

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
