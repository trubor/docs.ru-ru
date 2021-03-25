---
title: Руководство по программированию на C#. <exception>
description: Сведения о теге <exception> в XML. Этот тег позволяет указать, какие исключения могут быть созданы. Он может применяться к методам, свойствам, событиям и индексаторам.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 37d119e3cde115104d149d8f35b8937efddd70d4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479110"
---
# <a name="exception-c-programming-guide"></a>\<exception> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Параметры

- cref = "`member`"

  Ссылка на исключение, которое доступно из текущей среды компиляции. Компилятор проверяет, существует ли исключение, и приводит `member` к каноническому имени элемента в выходных XML-данных. `member` необходимо заключать в двойные кавычки (" ").

  См. подробнее о том, как форматировать `member`, чтобы создать ссылку на универсальный тип, в руководстве по [обработке XML-файла](processing-the-xml-file.md).

- `description`

  Описание исключения.

## <a name="remarks"></a>Примечания

Тег `<exception>` служит для указания возможных исключений. Этот тег может применяться к определениям методов, свойств, событий и индексаторов.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

Дополнительные сведения об обработке исключений см. в разделе [Исключения и обработка исключений](../exceptions/index.md).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](recommended-tags-for-documentation-comments.md)
