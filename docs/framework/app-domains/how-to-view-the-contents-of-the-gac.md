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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="40c57-103">Практическое руководство. Просмотр содержимого глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="40c57-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="40c57-104">Используйте [средство глобального кэша сборок (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) для просмотра содержимого глобального кэша сборок (GAC).</span><span class="sxs-lookup"><span data-stu-id="40c57-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="40c57-105">Просмотр сборок в GAC</span><span class="sxs-lookup"><span data-stu-id="40c57-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="40c57-106">Чтобы просмотреть список сборок в глобальном кэше сборок, откройте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell), а затем введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="40c57-106">To view a list of the assemblies in the global assembly cache, open a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="40c57-107">-или-</span><span class="sxs-lookup"><span data-stu-id="40c57-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="40c57-108">В предыдущих версиях .NET Framework с помощью расширения оболочки Windows [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) можно было просматривать глобальный кэш сборок в проводнике.</span><span class="sxs-lookup"><span data-stu-id="40c57-108">In earlier versions of .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="40c57-109">Начиная с версии .NET Framework 4 расширение оболочки Shfusion.dll является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="40c57-109">Beginning with .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="40c57-110">См. также</span><span class="sxs-lookup"><span data-stu-id="40c57-110">See also</span></span>

- [<span data-ttu-id="40c57-111">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="40c57-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="40c57-112">Gacutil.exe (программа глобального кэша сборок)</span><span class="sxs-lookup"><span data-stu-id="40c57-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
