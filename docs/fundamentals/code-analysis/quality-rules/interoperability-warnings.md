---
title: Правила переносимости и взаимодействия (анализ кода)
description: Узнайте больше о правилах анализа кода, связанных с переносимостью и взаимодействием
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592410"
---
# <a name="portability-and-interoperability-rules"></a>Правила переносимости и взаимодействия

Правила переносимости поддерживают возможность переноса между различными платформами. Правила взаимодействия поддерживают взаимодействие с клиентами COM.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
| - | - |
| [CA1401: методы P/Invoke не должны быть видимыми](ca1401.md) | Открытый или защищенный метод в открытом типе имеет атрибут System.Runtime.InteropServices.DllImportAttribute (также реализуется в Visual Basic с помощью ключевого слова Declare). Такие методы не следует делать видимыми. |
| [CA1416. Проверка совместимости платформ](ca1416.md) | При использовании в компоненте API, зависящего от платформы, код больше не будет работать на всех платформах. |
| [CA1417: не используйте `OutAttribute` в параметрах строки для P/Invokes](ca1417.md) | Если эта строка интернирована, строковые параметры, передаваемые по значению с `OutAttribute`, могут дестабилизировать среду выполнения. |
