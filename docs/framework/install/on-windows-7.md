---
title: Установка платформы .NET Framework в Windows 7 с пакетом обновления 1 (SP1)
description: Сведения об установке платформы .NET Framework в Windows 7 с пакетом обновления 1 (SP1).
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899091"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a><span data-ttu-id="0d127-103">Установка .NET Framework в Windows 7 с пакетом обновления 1 (SP1) и Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0d127-103">Install the .NET Framework on Windows 7 SP1 and Windows Server 2008 R2</span></span>

<span data-ttu-id="0d127-104">Для многих приложений, работающих в ОС Windows, требуется платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d127-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="0d127-105">Приведенные ниже инструкции помогут вам установить ее.</span><span class="sxs-lookup"><span data-stu-id="0d127-105">You can use the following instructions to install it.</span></span> <span data-ttu-id="0d127-106">Вы могли попасть на эту страницу после попытки запуска приложения и отображения следующего диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="0d127-106">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![Не удалось запустить это приложение.](./media/this-application-could-not-be-started.png)

<span data-ttu-id="0d127-108">Эти инструкции помогут вам установить необходимые версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d127-108">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="0d127-109">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) является самой новой версией.</span><span class="sxs-lookup"><span data-stu-id="0d127-109">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest version.</span></span> <span data-ttu-id="0d127-110">Она поддерживается в Windows 7 с пакетом обновления 1 (SP1) и Windows Server 2008 R2 и входит в состав [обновления Windows 10 за май 2019 г.](https://support.microsoft.com/help/4028685/windows-10-get-the-update)</span><span class="sxs-lookup"><span data-stu-id="0d127-110">It is supported on Windows 7 SP1 and Windows Server 2008 R2 and is included with [Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span></span>

## <a name="net-framework-48"></a><span data-ttu-id="0d127-111">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="0d127-111">.NET Framework 4.8</span></span>

> [!div class="button"]
> <span data-ttu-id="0d127-112">[скачать .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48).</span><span class="sxs-lookup"><span data-stu-id="0d127-112">[Download .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)</span></span>

<span data-ttu-id="0d127-113">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) можно использовать для запуска приложений, созданных для .NET Framework 4.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0d127-113">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) can be used to run applications built for .NET Framework 4.0 or later.</span></span>

### <a name="offline-installer"></a><span data-ttu-id="0d127-114">автономный установщик</span><span class="sxs-lookup"><span data-stu-id="0d127-114">Offline installer</span></span>

<span data-ttu-id="0d127-115">При выполнении автономной установки платформы .NET Framework в Windows 7 необходимо сначала убедиться, что на целевом компьютере установлена актуальная версия [Центра корневой сертификации Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm).</span><span class="sxs-lookup"><span data-stu-id="0d127-115">When doing an offline install for .NET Framework on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="0d127-116">Средство _certmgr.exe_ позволяет автоматизировать установку сертификата и его получение из Visual Studio или Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="0d127-116">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="0d127-117">Следующая команда используется для установки сертификата перед запуском установщика платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0d127-117">The following command is used to install the certificate before running the .NET Framework installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a><span data-ttu-id="0d127-118">.NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="0d127-118">.NET Framework 3.5</span></span>

<span data-ttu-id="0d127-119">Платформа [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) входит в состав Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0d127-119">The [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) is included with Windows 7.</span></span>

<span data-ttu-id="0d127-120">Платформа .NET Framework 3.5 поддерживает приложения, собранные для платформы .NET Framework версий с 1.0 по 3.5.</span><span class="sxs-lookup"><span data-stu-id="0d127-120">The .NET Framework 3.5 supports apps built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="help"></a><span data-ttu-id="0d127-121">Справка</span><span class="sxs-lookup"><span data-stu-id="0d127-121">Help</span></span>

<span data-ttu-id="0d127-122">Вы можете [обратиться за помощью в корпорацию Майкрософт](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help), если не можете определить правильную версию установленной платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d127-122">You can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) if you cannot get the correct version of the .NET Framework installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d127-123">См. также</span><span class="sxs-lookup"><span data-stu-id="0d127-123">See also</span></span>

- [<span data-ttu-id="0d127-124">Скачивание .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d127-124">Download the .NET Framework</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="0d127-125">Устранение неполадок с заблокированными установками и удалениями .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d127-125">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="0d127-126">Установка .NET Framework для разработчиков</span><span class="sxs-lookup"><span data-stu-id="0d127-126">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
