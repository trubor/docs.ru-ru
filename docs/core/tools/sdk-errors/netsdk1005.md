---
title: 'NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект'
description: Устранение проблемы отсутствия целевого объекта в файле ресурса.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717907"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="1d31f-103">NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект</span><span class="sxs-lookup"><span data-stu-id="1d31f-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="1d31f-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="1d31f-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="1d31f-105">Когда пакет SDK для .NET выдает ошибку NETSDK1005 или NETSDK1047, это означает, что в файле ресурсов проекта отсутствуют сведения об одной из целевых платформ.</span><span class="sxs-lookup"><span data-stu-id="1d31f-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="1d31f-106">Обычно это можно исправить, убедившись в том, что выполняется восстановление и что отсутствующее целевое значение включено в свойство `TargetFrameworks` проекта.</span><span class="sxs-lookup"><span data-stu-id="1d31f-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="1d31f-107">Известна проблема с ранними сборками предварительной версии 8 .NET 5 при использовании с предварительными версиями Visual Studio 16.8, которые привели к этой ошибке.</span><span class="sxs-lookup"><span data-stu-id="1d31f-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="1d31f-108">В частности, если отсутствующий целевой объект — это `net5.0-windows7.0` или `net5.0`, убедитесь, что выполнено обновление до последних версий Visual Studio и пакета SDK для .NET 5.</span><span class="sxs-lookup"><span data-stu-id="1d31f-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
