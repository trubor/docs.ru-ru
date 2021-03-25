---
description: Справочник по C#. Уровни доступности
title: Справочник по C#. Уровни доступности
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 509902e9998af421c0afd31070b1be36d64df0f8
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604597"
---
# <a name="accessibility-levels-c-reference"></a>Уровни доступности (Справочник по C#)

Модификаторы доступа `public`, `protected`, `internal` или `private` используются для указания одного из следующих объявленных уровней доступности к членам.  
  
|Объявленная доступность|Значение|  
|----------------------------|-------------|  
|[`public`](public.md)|Неограниченный доступ.|  
|[`protected`](protected.md)|Доступ ограничен содержащим классом или типами, которые являются производными от содержащего класса.|  
|[`internal`](internal.md)|Доступ ограничен текущей сборкой.|  
|[`protected internal`](protected-internal.md)|Доступ ограничен текущей сборкой или типами, которые являются производными от содержащего класса.|  
|[`private`](private.md)|Доступ ограничен содержащим типом.|  
|[`private protected`](private-protected.md)|Доступ ограничен содержащим классом или типами, которые являются производными от содержащего класса в текущей сборке. Доступно с версии C# 7.2. |  
  
 Вы можете указать для члена или типа только один модификатор доступа, за исключением случаев использования сочетаний `protected internal` или `private protected`.  
  
 Модификаторы доступа не могут быть указаны для пространств имен. Пространства имен не имеют ограничений доступа.  
  
 В зависимости от контекста, в котором производится объявление члена, допускаются только некоторые объявленные уровни доступности. Если модификатор доступа не указывается в объявлении члена, используется доступность по умолчанию.  
  
 Типы верхнего уровня, не вложенные в другие типы, могут иметь только уровень доступности `internal` или `public`. Для этих типов уровнем доступности по умолчанию является `internal`.  
  
 Вложенные типы, которые являются членами других типов, могут иметь объявленные уровни доступности, как указано в следующей таблице.  
  
|Члены типа|Уровень доступности членов по умолчанию|Допустимые объявленные уровни доступности члена|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|None|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`\*<br /><br /> `protected internal` <br /><br />`private protected`|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  

\* Элемент `interface` с доступностью типа `private` должен иметь реализацию по умолчанию.

Доступность вложенного типа зависит от [домена доступности](./accessibility-domain.md), который определяется объявленным уровнем доступности члена и доменом доступности непосредственно вмещающего его типа. Однако домен доступности вложенного типа не может выходить за границы домена доступности содержащего его типа.  
  
## <a name="c-language-specification"></a>Спецификация языка C#  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](./index.md)
- [Модификаторы доступа](./access-modifiers.md)
- [Домен доступности](./accessibility-domain.md)
- [Ограничения на использование уровней доступности](./restrictions-on-using-accessibility-levels.md)
- [Модификаторы доступа](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
