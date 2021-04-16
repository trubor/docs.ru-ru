---
title: Правила, касающиеся ненужного кода
description: Дополнительные сведения правилах, касающихся ненужного кода при анализе кода
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593858"
---
# <a name="unnecessary-code-rules"></a>Правила, касающиеся ненужного кода

Правила, касающиеся ненужного кода, определяют различные части базы кода, которые не нужны и могут быть подвергнуты рефакторингу или удалению. Наличие ненужного кода указывает на одну из следующих проблем:

- Удобочитаемость: присутствие ненужного кода ухудшает читаемость. Например, [IDE0001](ide0001.md) помечает ненужные квалификации type-name.
- Удобство сопровождения: необходимость обслуживать код, который больше не используется после рефакторинга и не нужен. Например, [IDE0051](ide0051.md) помечает неиспользуемые закрытые поля, свойства, события и методы.
- Производительность: ненужные вычисления, не имеющие побочных эффектов и ведущие к ненужным издержкам производительности. Например, [IDE0059](ide0059.md) помечает неиспользуемые назначения значений, когда выражение для расчета значения не имеет побочных эффектов.
- Функциональность: функциональная проблема в коде, в результате которой требуемый код становится избыточным. Например, [IDE0060](ide0060.md) помечает неиспользуемые параметры, когда метод случайно игнорирует входной параметр.

Правила в этом разделе относятся к следующим правилам, касающимся ненужного кода:

- [Упрощение имени (IDE0001)](ide0001.md)
- [Упрощение доступа для членов (IDE0002)](ide0002.md)
- [Удаление ненужных операций приведения (IDE0004)](ide0004.md)
- [Удаление ненужных операций импорта (IDE0005)](ide0005.md)
- [Удаление недоступного кода (IDE0035)](ide0035.md)
- [Удаление неиспользуемых закрытых членов (IDE0051)](ide0051.md)
- [Удаление непрочитанных закрытых членов (IDE0052)](ide0052.md)
- [Удаление ненужного значения выражения (IDE0058)](ide0058.md)
- [Удаление назначения лишних значений (IDE0059)](ide0059.md)
- [Удалите неиспользуемый параметр (IDE0060)](ide0060.md)
- [Удалить ненужное подавление (IDE0079)](ide0079.md)
- [Удаление ненужного оператора подавления (IDE0080)](ide0080.md) — только C#.
- [Удаление "ByVal" (IDE0081)](ide0081.md) — только Visual Basic.
- [Удаление ненужного оператора равенства (IDE0100)](ide0100.md)
- [Удаление ненужной пустой переменной (IDE0110)](ide0110.md) — только C#.

Некоторые из этих правил имеют параметры для настройки поведения правила:

- [csharp_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059)](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059)](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060)](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079)](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>См. также раздел

- [Правила языка для стиля кода](language-rules.md)
- [Справочник по правилам стиля кода](index.md)
