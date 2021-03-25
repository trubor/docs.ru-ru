---
title: <example> Руководство по программированию на C#.
description: Сведения о теге <example> в XML. Этот тег позволяет указать пример использования метода или другого элемента библиотеки.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 8f9b4fa4ac447b853008576a46be9beeb583b018
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479120"
---
# <a name="example-c-programming-guide"></a>\<example> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<example>description</example>
```

## <a name="parameters"></a>Параметры

- `description`

  Описание примера кода.

## <a name="remarks"></a>Примечания

Тег `<example>` позволяет указать пример использования метода или другого элемента библиотеки. Вместе с ним часто применяется тег [\<code>](./code.md).

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>См. также раздел

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
