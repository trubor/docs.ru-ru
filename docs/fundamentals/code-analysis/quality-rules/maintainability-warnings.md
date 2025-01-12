---
title: Правила удобства поддержки (анализ кода)
description: Узнайте больше о правилах удобства поддержки для анализа кода.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592407"
---
# <a name="maintainability-rules"></a>Правила удобства поддержки

Правила удобства поддержки распространяются на обслуживание библиотек и приложений.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
|-----------|-----------------------------------|
| [CA1501. Избегайте излишнего наследования](ca1501.md) | Тип расположен глубже четырех уровней в иерархии наследования. Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать. |
| [CA1502. Избегайте чрезмерной сложности](ca1502.md) | Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей. |
| [CA1505. Избегайте кода, неудобного для поддержки](ca1505.md) | Тип или метод имеет низкий индекс обслуживаемости. Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать. |
| [CA1506. Избегайте чрезмерной взаимозависимости классов](ca1506.md) | Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе. |
| [CA1507: Используйте nameof вместо строки](ca1507.md) | Строковый литерал используется в качестве аргумента, где можно использовать выражение `nameof`. |
| [CA1508: Избегайте появления неиспользуемого условного кода](ca1508.md) | Метод имеет код условия, который всегда вычисляется как `true` или `false` в среде выполнения. Это приводит к неиспользуемому коду в ветви `false` условия. |
| [CA1509: недопустимая запись в файле конфигурации метрик кода](ca1509.md) | Правила метрик кода, такие как [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) и [CA1506](ca1506.md), предоставили файл конфигурации с именем `CodeMetricsConfig.txt`, который имеет недопустимую запись. |

## <a name="see-also"></a>См. также раздел

- [Оценка сложности и удобства сопровождения управляемого кода](/visualstudio/code-quality/code-metrics-values)
