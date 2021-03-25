---
title: <value> Руководство по программированию на C#.
description: Сведения о теге <value> в XML. Этот тег позволяет описать значение, которое представляется свойством.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477641"
---
# <a name="value-c-programming-guide"></a>\<value> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Параметры

- `property-description`

  Описание свойства.

## <a name="remarks"></a>Примечания

Тег `<value>` позволяет описывать значение, которое представляется свойством. При добавлении свойства с помощью мастера создания кода из среды разработки Visual Studio .NET для нового свойства будет добавлен тег [\<summary>](./summary.md). После этого следует вручную добавить тег `<value>` для описания значения, которое представляется свойством.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
