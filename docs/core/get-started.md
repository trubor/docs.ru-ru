---
title: Начало работы с .NET
description: Создание приложения .NET "Hello World".
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.topic: tutorial
ms.openlocfilehash: 1c88817b0503b050faf2a7ce3bd42d892931a698
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740388"
---
# <a name="get-started-with-net"></a>Начало работы с .NET

В этой статье объясняется, как создать и запустить приложение .NET "Hello World!".

Если вы не знаете, что такое .NET, начните с раздела о [знакомстве с .NET](introduction.md).

## <a name="create-an-application"></a>Создание приложения

Сначала скачайте и установите [пакет SDK для .NET](https://dotnet.microsoft.com/download/dotnet) на компьютер.

Затем откройте окно терминала, например **PowerShell**, **командную строку** или **bash**. Для создания и запуска приложения C# введите следующие команды `dotnet`:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Вы увидите такой результат:

```output
Hello World!
```

Поздравляем! Вы создали простое приложение .NET.

## <a name="next-steps"></a>Дальнейшие действия

Начните разработку приложений .NET со знакомства с [пошаговым руководством](../standard/get-started.md) или с просмотра [видеороликов о .NET](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) на YouTube.
