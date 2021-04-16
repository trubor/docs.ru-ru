---
title: Правила документирования (анализ кода)
description: Дополнительные сведения о правилах документирования для анализа кода
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592665"
---
# <a name="documentation-rules"></a>Правила документирования

Правила документации поддерживают написание хорошо задокументированных библиотек путем правильного использования [комментариев XML-документации](../../../csharp/codedoc.md) для видимых извне API-интерфейсов.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
| - | - |
| [CA1200: Избегайте использования тегов cref с префиксом](ca1200.md) | Атрибут [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) в теге XML-документации означает "code reference" (кодовая ссылка). Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство. Старайтесь не использовать теги `cref` с префиксами, так как это не позволяет компилятору проверять ссылки. Это также мешает поиску и обновлению этих символьных ссылок во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio. |
