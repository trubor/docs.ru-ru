---
title: <remarks> Руководство по программированию на C#.
description: Сведения о теге <remarks> в XML. Этот тег позволяет добавить сведения о типе, дополняющие информацию, которая указана с помощью <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 2227dd8bd4d81f5fda8cf529e18c7a613cca6b8e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477824"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Параметры

- `Description`

  Описание элемента.

## <a name="remarks"></a>Примечания

Тег `<remarks>` позволяет добавить сведения о типе, дополняющие информацию, указанную с помощью тега [\<summary>](./summary.md). Эти сведения отображаются в окне "Обозреватель объектов".

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>См. также раздел

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
