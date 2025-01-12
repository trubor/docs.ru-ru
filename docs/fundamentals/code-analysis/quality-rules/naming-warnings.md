---
title: Правила именования (анализ кода)
description: Сведения о правилах именования в анализе кода.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis rules, naming rules
- naming rules
- rules, naming
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 57524fbff364fd03a90b90a0900bd17e9c8a9248
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "99732323"
---
# <a name="naming-rules"></a>Правила именования

Правила именования поддерживают соблюдение [соглашений об именовании в соответствии с рекомендациями по проектированию .NET](../../../standard/design-guidelines/naming-guidelines.md).

## <a name="in-this-section"></a>Содержание раздела

|Правило|Описание|
|----------|-----------------|
|[CA1700. Не присваивайте перечисляемым значениям имя Reserved](ca1700.md)|В данном правиле предполагается, что член перечисления, имя которого содержит слово "reserved", не используется в настоящее время, а является местозаполнителем, который будет в дальнейшем переименован или удален. Переименование или удаление элемента — это критическое изменение.|
|[CA1707. Идентификаторы не должны содержать символы подчеркивания](ca1707.md)|В соответствии с соглашением имена идентификаторов не могут содержать знак подчеркивания (_). Это правило позволяет проверить пространства имен, типы, элементы и параметры.|
|[CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами](ca1708.md)|Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков.|
|[CA1710. Идентификаторы должны иметь правильные суффиксы](ca1710.md)|По соглашению имена типов, расширяющих определенные базовые типы или реализующих определенные интерфейсы, а также типов, являющихся производными от первых, имеют суффикс, связанный с базовым типом или интерфейсом.|
|[CA1711. Идентификаторы не должны иметь неправильные суффиксы](ca1711.md)|В соответствии с соглашением об именовании, определенные зарезервированные суффиксы должны добавляться только к именам типов, которые расширяют некоторые базовые типы или реализуют определенные интерфейсы, а также производных от них типов. В именах других типов зарезервированные суффиксы использоваться не должны.|
|[CA1712. Не добавляйте имя типа перед перечисляемыми значениями](ca1712.md)|Имена элементов перечисления не должны содержать префиксы с именем типа, так как сведения о типе предоставляются средствами разработки.|
|[CA1713. События не должны иметь префикс before или after](ca1713.md)|Имя события начинается с Before или After. Чтобы дать имена связанным событиям, возникающим в определенной последовательности, используйте настоящее или прошедшее время, чтобы обозначить положение события в последовательности действий.|
|[CA1714. У перечислений флагов должны быть имена во множественном числе](ca1714.md)|Открытое перечисление содержит атрибут System.FlagsAttribute, и имя перечисления не заканчивается на "s". Имена типов, помеченных атрибутом FlagsAttribute, используются во множественном числе, поскольку данный атрибут указывает на возможность задания нескольких значений.|
|[CA1715. Идентификаторы должны иметь правильные префиксы](ca1715.md)|Имя доступного для внешнего кода интерфейса не начинается с заглавной буквы "I".  Имя параметра универсального типа в доступном для внешнего кода типе или методе не начинается с заглавной буквы "Т".|
|[CA1716. Идентификаторы не должны совпадать с ключевыми словами](ca1716.md)|Имя пространства имен или типа совпадает с ключевым словом, зарезервированным в языке программирования. Идентификаторы пространств имен и типов не должны совпадать с ключевыми словами, определенными в языках, поддерживаемых в среде CLR.|
|[CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе](ca1717.md)|Согласно правилам именования множественное число имени перечисления указывает, что одновременно можно задать несколько значений перечисления.|
|[CA1720. Идентификаторы не должны содержать имена типов](ca1720.md)|Имя параметра в доступном для внешнего кода элементе содержит имя типа данных, или имя доступного для внешнего кода элемента содержит языковое имя типа данных.|
|[CA1721. Имена свойств не должны совпадать с именами методов get](ca1721.md)|Имя открытого или защищенного элемента начинается с Get и соответствует имени открытого или защищенного свойства и по другим параметрам. Методы Get и свойства должны иметь имена, позволяющие четко различать их функции.|
|[CA1724. Имена типов не должны совпадать с именами пространства имен](ca1724.md)|Имена типов не должны совпадать с именами пространства имен .NET. Нарушение этого правила приводит к сокращению функциональности библиотеки.|
|[CA1725. Имена параметров должны соответствовать базовому объявлению](ca1725.md)|Согласованное именование параметров в иерархии переопределений увеличивает удобство использования переопределений метода. Если имя параметра в производном методе отличается от имени в базовом объявлении, может возникнуть путаница в определении того, чем является метод: переопределением базового метода или новой перегрузкой.|
