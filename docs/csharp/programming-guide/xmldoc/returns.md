---
title: <returns> Руководство по программированию на C#.
description: Сведения о теге <returns> в XML. Этот тег используется в комментариях к объявлению метода для описания возвращаемого значения.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 6a098208a51ca31fe2278b7c696deb15a13f8e1e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477805"
---
# <a name="returns-c-programming-guide"></a>\<returns> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Параметры

- `description`

  Описание возвращаемого значения.

## <a name="remarks"></a>Примечания

Тег `<returns>` следует использовать в комментариях к объявлению метода для описания возвращаемого значения.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
