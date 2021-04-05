---
title: Руководство по программированию на C#. Явная реализация интерфейса
description: Класс может реализовывать интерфейсы, которые содержат член с такой же сигнатурой в C#. Явная реализация создает член класса, относящийся к одному интерфейсу.
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610867"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Явная реализация интерфейса (Руководство по программированию в C#)

Если [класс](../../language-reference/keywords/class.md) реализует два интерфейса, содержащих член с одинаковой сигнатурой, при реализации такого члена в классе оба интерфейса будут использовать этот член в качестве собственной реализации. В следующем примере все вызовы `Paint` приводят к вызову одного и того же метода. Первый пример определяет типы:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Следующий пример вызывает методы:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Но может потребоваться, чтобы одна и та же реализация вызывалась для обоих интерфейсов. Чтобы вызывать разную реализацию в зависимости от используемого интерфейса, можно явно реализовать член интерфейса. Явная реализация интерфейса — это член класса, который вызывается только через указанный интерфейс. Укажите имя интерфейса и точку в качестве префикса в имени члена класса. Пример:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Член класса `IControl.Paint` доступен только через интерфейс `IControl`, а `ISurface.Paint` — только через интерфейс `ISurface`. Обе реализации метода будут разделены, и ни одна из них не будет доступна в классе напрямую. Пример:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Явная реализация также применяется в случаях, когда в каждом из двух интерфейсов объявляются разные члены (например, свойство и метод) с одинаковыми именами. Чтобы реализовать оба интерфейса и избежать ошибок компилятора, класс должен использовать явную реализацию либо свойства `P`, либо метода `P`, либо одновременно обоих этих членов. Пример:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Явная реализация интерфейса не имеет модификатора доступа, так как она недоступна в качестве члена типа, в котором определена. Вместо этого она доступна только при вызове через экземпляр интерфейса. При указании модификатора доступа для явной реализации интерфейса возникает ошибка компилятора [CS0106](../../language-reference/compiler-messages/cs0106.md). Дополнительные сведения см. в разделе [`interface` (справочник по C#)](../../language-reference/keywords/interface.md).

Начиная с версии [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), вы можете определять реализацию для членов, объявленных в интерфейсе. Если класс наследует реализацию метода от интерфейса, этот метод доступен только через ссылку типа интерфейса. Наследуемый член не отображается как часть открытого интерфейса. Следующий пример определяет реализацию по умолчанию для метода интерфейса:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Следующий пример вызывает реализацию по умолчанию:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Любой класс, реализующий интерфейс `IControl`, может переопределить метод `Paint` по умолчанию либо в качестве открытого метода, либо в качестве реализации интерфейса.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Классы и структуры](../classes-and-structs/index.md)
- [Интерфейсы](./index.md)
- [Наследование](../classes-and-structs/inheritance.md)
