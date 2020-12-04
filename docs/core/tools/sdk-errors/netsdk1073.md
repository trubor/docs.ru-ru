---
title: 'NETSDK1073: элемент FrameworkReference не распознан'
description: Устранение проблемы, когда не удается найти элемент FrameworkReference.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713032"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="25127-103">NETSDK1073: элемент FrameworkReference не распознан</span><span class="sxs-lookup"><span data-stu-id="25127-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="25127-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="25127-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="25127-105">Эта ошибка обычно означает, что существует версия определенного элемента FrameworkReference, которую пакет SDK не может найти.</span><span class="sxs-lookup"><span data-stu-id="25127-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="25127-106">Попробуйте удалить папки *obj* и *bin* и запустите `dotnet restore`, чтобы повторно скачать последние пакеты.</span><span class="sxs-lookup"><span data-stu-id="25127-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="25127-107">Кроме того, может возникнуть ошибка установки, поэтому убедитесь, что вы используете последние версии .NET и Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25127-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
