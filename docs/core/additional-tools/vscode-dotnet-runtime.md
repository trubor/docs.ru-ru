---
title: Средство установки .NET для авторов расширений VS Code
description: Обзор средства установки .NET для авторов расширений, которое представляет собой расширение Visual Studio Code для установки среды выполнения .NET.
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: 4be931a254e4ce969f9eaf2efde7939cb54e1d5f
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605156"
---
# <a name="net-install-tool-for-extension-authors"></a>Средство установки .NET для авторов расширений

[Средство установки .NET для авторов расширений](https://github.com/dotnet/vscode-dotnet-runtime) — это расширение Visual Studio Code, которое позволяет получить среду выполнения .NET специально для разработчиков расширений VS Code. Это средство предназначено для использования в расширениях, написанных на .NET. Для работы с ним требуется загрузить части расширений (например, языковой сервер) с помощью .NET. Расширение не предназначено для непосредственного использования пользователями при установке .NET для разработки.

## <a name="getting-started-extension-authors"></a>Начало работы. Авторы расширений

Чтобы убедиться, что средство установки .NET для авторов расширений подходит для вашего сценария, ознакомьтесь с [основными задачами этого расширения](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) на нашей странице GitHub.

> [!NOTE]
> С помощью этого средства можно установить только среду выполнения .NET. В настоящее время оно не поддерживает установку пакета SDK для .NET.

Убедившись, что средство установки .NET для авторов расширений соответствует вашим требованиям, можете установить зависимость от него в [манифесте расширения](https://code.visualstudio.com/api/references/extension-manifest) и начать использовать команды, предоставляемые в [API VS Code](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command). Список команд, предоставляемых этим расширением, можно найти [на нашей странице GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).

Ознакомьтесь с этим [примером расширения](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample), чтобы увидеть, как применяются эти инструкции.

Дополнительные примеры см. в следующих разделах с описанием расширений с открытым кодом, которые используют это средство:

- [Средства Azure Resource Manager (ARM) для Visual Studio Code](https://github.com/microsoft/vscode-azurearmtools)

- [Записные книжки для .NET Interactive](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a>Начало работы. Пользователи

Как правило, пользователю не нужно взаимодействовать со средством установки .NET для авторов расширений. Если у вас возникли проблемы с расширением, ознакомьтесь со страницей с инструкциями по [устранению неполадок](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting-runtime.md) или сообщите о проблеме на нашей странице [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).
