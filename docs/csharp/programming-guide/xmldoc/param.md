---
title: <param> Руководство по программированию на C#.
description: Сведения о теге <param> в XML. Этот тег используется в комментариях к объявлению метода для описания одного из параметров такого метода.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 1385365b2cdf18563686fdf4a5a1b17b89feafcd
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477996"
---
# <a name="param-c-programming-guide"></a>\<param> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра метода. Имя заключается в двойные кавычки (" ").

- `description`

  Описание параметра.

## <a name="remarks"></a>Примечания

Тег `<param>` следует использовать в комментариях к объявлению метода для описания одного из параметров такого метода. Чтобы задокументировать несколько параметров, используйте несколько тегов `<param>`.

Текст тега `<param>` отображается в IntelliSense, обозревателе объектов и веб-отчете по комментариям к коду.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
