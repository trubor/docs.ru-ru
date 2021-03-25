---
title: Руководство по программированию на C#. <see>
description: Сведения о теге <see> в XML. Этот тег позволяет указать ссылку в тексте, например с помощью атрибута cref.
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477777"
---
# <a name="see-c-programming-guide"></a>\<see> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Параметры

- cref = "`member`"

  Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции. Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных. *member* необходимо заключать в двойные кавычки (" ").

## <a name="remarks"></a>Примечания

Тег `<see>` позволяет задать ссылку из текста. С помощью тега [\<seealso>](./seealso.md) можно указать, что текст должен быть размещен в разделе "См. также". Используйте [cref Attribute](./cref-attribute.md) для создания внутренних гиперссылок на страницы документации для элементов кода. Кроме того, ``href`` является допустимым атрибутом, который будет функционировать как гиперссылка.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

В следующем примере показан тег `<see>` в разделе сводки.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
