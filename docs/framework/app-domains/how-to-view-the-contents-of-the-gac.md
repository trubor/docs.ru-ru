---
title: Практическое руководство. Просмотр содержимого глобального кэша сборок
description: Сведения о просмотре содержимого глобального кэша сборок в .NET с помощью средства глобального кэша сборок (gacutil.exe).
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: a40c371e6f95f6c90ecbfbf28183226632a58e5b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258316"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Практическое руководство. Просмотр содержимого глобального кэша сборок

Используйте [средство глобального кэша сборок (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) для просмотра содержимого глобального кэша сборок (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Просмотр сборок в GAC

Чтобы просмотреть список сборок в глобальном кэше сборок, откройте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell), а затем введите следующую команду:

```shell
gacutil -l
```

-или-

```shell
gacutil /l
```

> [!NOTE]
> В предыдущих версиях .NET Framework с помощью расширения оболочки Windows [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) можно было просматривать глобальный кэш сборок в проводнике. Начиная с версии .NET Framework 4 расширение оболочки Shfusion.dll является устаревшим.

## <a name="see-also"></a>См. также

- [Работа со сборками и глобальным кэшем сборок](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (программа глобального кэша сборок)](../tools/gacutil-exe-gac-tool.md)
