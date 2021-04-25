---
title: <seealso> Руководство по программированию на C#.
description: Сведения об использовании тега <seealso> в XML. Этот тег позволяет указать текст, который должен отображаться в разделе "См. также".
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 35420536ef14e91dcf8bf904573ab758d5448a63
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494106"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```csharp
/// <seealso cref="member"/>
// or
/// <seealso href="link">Link Text</seealso>
```

## <a name="parameters"></a>Параметры

- `cref="member"`

  Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции. Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных. `member` необходимо заключать в двойные кавычки (" ").

  Сведения о создании ссылки cref на универсальный тип см. в статье об [атрибуте cref](./cref-attribute.md).

- `href="link"`

  Гиперссылка на заданный URL-адрес. Например, `<seealso href="https://github.com">GitHub</seealso>` формирует гиперссылку с текстом :::no-loc text="GitHub":::, которая ведет на сайт `https://github.com`.

## <a name="remarks"></a>Примечания

С помощью тега `<seealso>` можно указать текст, который должен отображаться в разделе "См. также". Тег [\<see>](./see.md) позволяет задать ссылку из текста.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

См. [\<summary>](./summary.md) с примером использования \<seealso>.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
