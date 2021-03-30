---
title: Выражение with в справочнике по C#
description: Сведения о выражении with, которое выполняет обратимое изменение записей C#
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 24b9fdfcef6fe042204217323bb09c047c58296c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872539"
---
# <a name="with-expression-c-reference"></a>Выражение with (справочник по C#)

Выражение `with`, доступное в C# 9.0 и более поздних версиях, создает копию операнда [record](../builtin-types/record.md) с измененными заданными свойствами и полями:

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

Как показано в предыдущем примере, для указания элементов для изменения и их новых значений используется синтаксис [инициализатора объектов](../../programming-guide/classes-and-structs/object-and-collection-initializers.md). В выражении `with` левый операнд должен иметь тип записи.

Результат выражения `with` имеет тот же тип среды выполнения, что и операнд выражения, как показано в следующем примере:

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

В случае с членом ссылочного типа при копировании записи копируется только ссылка на экземпляр. Как скопированный, так и исходный экземпляр записи имеют доступ к одному и тому же экземпляру ссылочного типа. В следующем примере продемонстрировано такое поведение.

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

Любой тип записи имеет *конструктор копии*. Это конструктор с одним параметром содержащего типа записи. Он копирует состояние своего аргумента в новый экземпляр записи. При вычислении выражения `with` вызывается конструктор копий для создания нового экземпляра записи на основе исходной записи. После этого новый экземпляр обновляется в соответствии с указанными изменениями. По умолчанию конструктор копий является неявным, то есть созданным компилятором. Если необходимо настроить семантику копирования записей, явно объявите конструктор копии с требуемым поведением. В следующем примере предыдущий пример обновляется явным образом с помощью конструктора копии. Новое поведение копирования записи заключается в копировании элементов списка вместо ссылки на список:

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах [примечания к предлагаемой функции записи](~/_csharplang/proposals/csharp-9.0/records.md):

- [Выражение `with`](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [Копирование и клонирование членов](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a>См. также раздел

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Записи](../builtin-types/record.md)
