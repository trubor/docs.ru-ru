---
title: <para> Руководство по программированию на C#.
description: Сведения о теге <para> в XML. Этот тег позволяет добавить структуру к тексту в другом теге, например <summary>, <remarks>или <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 5cb1c22dceae7a45a47fcb8807303d11e1220935
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478005"
---
# <a name="para-c-programming-guide"></a>\<para> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<para>content</para>
```

## <a name="parameters"></a>Параметры

- `content`

  Текст абзаца.

## <a name="remarks"></a>Примечания

Тег `<para>` используется внутри другого тега, например [\<summary>](./summary.md), [\<remarks>](./remarks.md) или [\<returns>](./returns.md), и позволяет добавить к тексту структуру.

Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).

## <a name="example"></a>Пример

См. [\<summary>](./summary.md) с примером использования `<para>`.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
