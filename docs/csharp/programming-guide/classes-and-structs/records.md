---
title: Записи. Руководство по программированию в C#
description: Сведения о типах записей и их создании
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: a45ed08da18e58f11793d6874d7275d9f5216be4
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260042"
---
# <a name="records-c-programming-guide"></a>Записи (Руководство по программированию в C#)

[Запись](../../language-reference/builtin-types/record.md) — это [класс](../../language-reference/keywords/class.md), предоставляющий специальный синтаксис и поведение для работы с моделями данных. Дополнительные сведения о классах см. в разделе [Классы (руководство по программированию на C#)](classes.md).

## <a name="when-to-use-records"></a>Когда следует использовать записи

Рекомендуется использовать запись вместо класса в следующих сценариях.

* Необходимо определить ссылочный тип, для которого объекты являются неизменяемыми.
* Необходимо определить модель данных, зависящую от [равенства значений](../statements-expressions-operators/equality-comparisons.md#value-equality).

### <a name="immutability"></a>Неизменяемость

Неизменяемый тип — это тип, который не позволяет изменять значения свойств или полей объекта после его создания. Неизменность может быть полезной, если требуется обеспечить потокобезопасность типа или если существует зависимость от хэш-кода, остающегося неизменным в хэш-таблице. Записи предоставляют краткий синтаксис для создания неизменяемых типов и работы с ними.

Неизменяемость подходит не для всех сценариев данных. [Entity Framework Core](/ef/core/), например, не поддерживает обновление с неизменяемыми типами сущностей.

### <a name="value-equality"></a>Равенство значений

Для записей равенство значений означает, что две переменные типа "запись" равны, если совпадают типы и все значения свойств и полей. Для других ссылочных типов, таких как классы, равенство означает [равенство ссылок](../statements-expressions-operators/equality-comparisons.md#reference-equality). То есть две переменные типа "класс" равны, если они ссылаются на один и тот же объект. Методы и операторы, определяющие равенство двух экземпляров записи, используют равенство значений.

Не все модели данных хорошо работают с равенством значений. Например, [Entity Framework Core](/ef/core/) опирается на равенство ссылок, чтобы гарантировать, что в нем используется только один экземпляр типа сущности для того, что является концептуально одной сущностью. По этой причине типы записей не подходят для использования в качестве типов сущностей в Entity Framework Core.

## <a name="how-records-differ-from-classes"></a>Отличия записей от классов

Тот же синтаксис, который [объявляет](classes.md#declaring-classes) и [создает экземпляры](classes.md#creating-objects) классов, можно использовать с записями. Просто замените ключевое слово `record` на `class`. Аналогично, записями поддерживается тот же синтаксис для выражения связей наследования. Записи отличаются от классов следующим образом.

* Для объявления и создания экземпляра типа с неизменяемыми свойствами можно использовать [позиционные параметры](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition).
* Те же методы и операторы, которые указывают на равенство или неравенство ссылок в классах (например <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> и `==`), указывают на [равенство или неравенство значений](../../language-reference/builtin-types/record.md#value-equality) в записях.
* Можно использовать [выражение `with`](../../language-reference/builtin-types/record.md#nondestructive-mutation) для создания копии неизменяемого объекта с новыми значениями в выбранных свойствах.
* Метод записи `ToString` создает форматированную строку, содержащую имя типа объекта, а также имена и значения всех его открытых свойств.
* Запись может [наследовать от другой записи](../../language-reference/builtin-types/record.md#inheritance). Запись не может наследовать от класса, а класс не может наследовать от записи.

## <a name="examples"></a>Примеры

В следующем примере определяется открытая запись, которая использует позиционные параметры для объявления и создания экземпляра. Затем в нем выводятся имя типа и значения свойств:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

В следующем примере демонстрируется равенство значений в записях:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

В следующем примере показано использование выражения `with` для копирования неизменяемого объекта и изменения одного из свойств:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

Дополнительные сведения см. в разделе [Записи (справочник по C#)](../../language-reference/builtin-types/record.md).
  
## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также

- [Классы (Руководство по программированию на C#)](classes.md)
- [Записи (справочник по C#)](../../language-reference/builtin-types/record.md).
- [Руководство по программированию на C#](../index.md)
- [Объектно-ориентированное программирование](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [Полиморфизм](polymorphism.md)
- [Имена идентификаторов](../inside-a-program/identifier-names.md)
- [Члены](members.md)
- [Методы](methods.md)
- [Конструкторы](constructors.md)
- [Методы завершения](destructors.md)
- [Объекты](objects.md)
