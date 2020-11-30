---
title: Развертывание .NET Framework
description: Узнайте, как развертывать .NET для разработчиков, которые хотят устанавливать .NET вместе с приложениями, а также для администраторов, которые хотят развертывать .NET по сети.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: b42646b60fab91fe761a8fdef59d67be6ffa884b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242049"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="9e00f-103">Развертывание .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9e00f-103">Deploying the .NET Framework</span></span>

<span data-ttu-id="9e00f-104">В этом разделе документации по платформе .NET Framework предоставлены сведения для разработчиков, которые хотят установить платформу .NET Framework для своих приложений, и для разработчиков, которые хотят развернуть платформу .NET Framework по сети.</span><span class="sxs-lookup"><span data-stu-id="9e00f-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="9e00f-105">В ней также рассмотрены вопросы активации и перезапуска, связанные с развертыванием, и описано, как отслеживать ход установки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e00f-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e00f-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="9e00f-106">In This Section</span></span>  

 [<span data-ttu-id="9e00f-107">Руководство по развертыванию для разработчиков</span><span class="sxs-lookup"><span data-stu-id="9e00f-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="9e00f-108">Описываются способы установки .NET Framework на компьютеры пользователей вместе с приложениями.</span><span class="sxs-lookup"><span data-stu-id="9e00f-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="9e00f-109">Руководство по развертыванию для администраторов</span><span class="sxs-lookup"><span data-stu-id="9e00f-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="9e00f-110">Инструкции для системного администратора по развертыванию платформы .NET Framework и ее системных зависимостей в сети с помощью Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9e00f-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="9e00f-111">Уменьшение числа перезагрузок при установке платформы .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9e00f-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="9e00f-112">Описывается диспетчер перезапуска, который по возможности предотвращает перезагрузки, и его преимущества для приложений, устанавливающих платформу .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e00f-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="9e00f-113">Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9e00f-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="9e00f-114">Описывается автоматический запуск и отслеживание процесса установки .NET Framework с выводом собственного представления хода выполнения установки.</span><span class="sxs-lookup"><span data-stu-id="9e00f-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="9e00f-115">Ошибки инициализации платформы .NET Framework. Управление пользовательской средой</span><span class="sxs-lookup"><span data-stu-id="9e00f-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="9e00f-116">В этой статье объясняется, что происходит, когда приложению .NET Framework требуется версия среды CLR, которая является недопустимой или не установлена на компьютере пользователя. Также описано, как устранить эти ошибки и как управлять сообщением об ошибке, которое отображается для пользователя.</span><span class="sxs-lookup"><span data-stu-id="9e00f-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="9e00f-117">Практическое руководство. Отладка проблем при активации среды CLR</span><span class="sxs-lookup"><span data-stu-id="9e00f-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="9e00f-118">В этой статье объясняется, как просматривать и отлаживать журналы активации среды CLR, чтобы решить проблемы, с которыми вы можете столкнуться при настройке запуска приложения с необходимой версией CLR.</span><span class="sxs-lookup"><span data-stu-id="9e00f-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e00f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="9e00f-119">See also</span></span>

- [<span data-ttu-id="9e00f-120">Руководство по разработке</span><span class="sxs-lookup"><span data-stu-id="9e00f-120">Development Guide</span></span>](../development-guide.md)
