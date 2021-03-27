---
title: NETSDK1059. Проект содержит устаревшее средство .NET CLI
description: Устранение проблемы с проектом, содержащим устаревший инструмент .NET CLI.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: cad546ed1636b71be6b77aa00ef2f3a20095daa5
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653040"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059. Проект содержит устаревшее средство .NET CLI

**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий

Если пакет SDK для .NET выдает предупреждение NETSDK1059, значит, ваш проект содержит устаревшее средство .NET CLI. Начиная с .NET Core 2.1 эти средства включены в пакет SDK для .NET, и в проекте не требуется явная ссылка на них. Дополнительные сведения см. в разделе [Средства проекта теперь включены в пакет SDK](../../compatibility/2.1.md#project-tools-now-included-in-sdk).
