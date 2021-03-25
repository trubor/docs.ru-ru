---
title: <typeparam> Руководство по программированию на C#.
description: Сведения о теге <typeparam> в XML. Этот тег используется в комментариях к объявлению универсального типа или метода для описания параметра типа.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 1b9d5d30c1a507e3bb7938ee0c036cdac3ef2f90
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477682"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра типа. Имя заключается в двойные кавычки (" ").

- `description`

  Описание параметра типа.

## <a name="remarks"></a>Примечания

Тег `<typeparam>` следует использовать в комментариях к объявлению универсального типа или метода для описания параметра типа. Добавьте такой тег для каждого параметра типа универсального типа или метода.

Дополнительные сведения см. в статье [Универсальные шаблоны](../generics/index.md).

Текст тега `<typeparam>` будет отображаться в IntelliSense, (веб-отчет по комментариям к коду в [окне обозревателя объектов](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)).

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>См. также раздел

- [справочник по C#](../../language-reference/index.md)
- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
