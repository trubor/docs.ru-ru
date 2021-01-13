---
title: 'NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект'
description: Устранение проблемы отсутствия целевого объекта в файле ресурса.
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678170"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="4c2c0-103">NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект</span><span class="sxs-lookup"><span data-stu-id="4c2c0-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="4c2c0-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="4c2c0-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="4c2c0-105">Когда пакет SDK для .NET выдает ошибку NETSDK1005 или NETSDK1047, это означает, что в файле ресурсов проекта отсутствуют сведения об одной из целевых платформ.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="4c2c0-106">NuGet записывает файл с именем *project.assets.json* в папку *obj*, а пакет SDK для .NET использует его для получения сведений о пакетах для передачи в компилятор.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-106">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="4c2c0-107">В .NET 5 в NuGet добавлено новое поле с именем `TargetFrameworkAlias`, поэтому более ранние версии MSBuild или NuGet создают файл ресурсов без нового поля.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-107">In .NET 5, NuGet added a new field named `TargetFrameworkAlias`, so earlier versions of MSBuild or NuGet generate an assets file without the new field.</span></span> <span data-ttu-id="4c2c0-108">Дополнительные сведения см. в разделе [Ошибка NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span><span class="sxs-lookup"><span data-stu-id="4c2c0-108">For more information, see [error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span></span>

<span data-ttu-id="4c2c0-109">Ниже приведены некоторые действия, которые можно выполнить, чтобы устранить ошибку.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-109">Here are some actions you can take that may resolve the error:</span></span>

* <span data-ttu-id="4c2c0-110">Убедитесь, что вы используете MSBuild версии 16.8 или более поздней, а также NuGet версии 5.8 или более поздней, и восстановите проект после обновления средств.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-110">Make sure that you're using MSBuild version 16.8 or later and NuGet version 5.8 or later, and restore the project after updating your tools.</span></span> <span data-ttu-id="4c2c0-111">При использовании NuGet версии 5.8 или более поздней следует использовать Visual Studio 2019 версии 16.8 или более поздней, MSBuild версии 16.8 или более поздней, а также пакет SDK для .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-111">When you're using NuGet version 5.8 or later, you should be using Visual Studio 2019 version 16.8 or later, MSBuild version 16.8 or later, and .NET 5.0 SDK or later.</span></span>

* <span data-ttu-id="4c2c0-112">Если при сборке проекта в Visual Studio 2019 ошибка возникает впервые после установки версии 16.8 или после изменения целевой платформы проекта, выполните сборку еще раз.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-112">If you get the error while building a project in Visual Studio 2019 for the first time after installing version 16.8 or after changing the project's target framework, build the project a second time.</span></span>

* <span data-ttu-id="4c2c0-113">Перед сборкой проекта удалите папку *obj*.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-113">Delete the *obj* folder before building the project.</span></span>

* <span data-ttu-id="4c2c0-114">Убедитесь, что отсутствующее целевое значение включено в свойство `TargetFrameworks` проекта.</span><span class="sxs-lookup"><span data-stu-id="4c2c0-114">Make sure that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>
