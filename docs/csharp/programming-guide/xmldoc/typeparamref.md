---
title: Руководство по программированию на C#. <typeparamref>
description: Сведения о теге <typeparamref> в XML. Этот тег разрешает получателям файла документации форматировать слово определенным образом, например курсивным шрифтом.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 1bb9a73f4122f3b9d521565a7172a9b8f75f7a98
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477664"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра типа. Имя заключается в двойные кавычки (" ").

## <a name="remarks"></a>Примечания

Дополнительные сведения о параметрах типа в универсальных типах и методах см. в разделе [Универсальные шаблоны](../generics/index.md).

Используйте этот тег, чтобы разрешить получателям файла документации форматировать слово определенным образом, например курсивным шрифтом.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
