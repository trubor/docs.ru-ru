---
title: Практическое руководство. Назначение службам контекста безопасности
description: Назначайте службам контекста безопасности. Службы, выполняемые в контексте системной учетной записи по умолчанию, и вошедший в систему пользователь имеют разные права доступа к системным ресурсам.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
ms.openlocfilehash: dcf0680f1bcb0f0e927bdb37ea56f7b3025be09b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270541"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="860e9-104">Практическое руководство. Назначение службам контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="860e9-104">How to: Specify the Security Context for Services</span></span>

<span data-ttu-id="860e9-105">По умолчанию службы работают в контексте безопасности, отличном от того, в котором работает вошедший в систему пользователь.</span><span class="sxs-lookup"><span data-stu-id="860e9-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="860e9-106">Службы работают в контексте стандартной системной учетной записи с именем `LocalSystem`. Она дает им другие права на доступ к системным ресурсам (не такие, как у пользователя).</span><span class="sxs-lookup"><span data-stu-id="860e9-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="860e9-107">Эту ситуацию можно изменить, указав другую учетную запись пользователя, под которой будет работать служба.</span><span class="sxs-lookup"><span data-stu-id="860e9-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="860e9-108">Чтобы задать контекст безопасности, для процесса, в котором выполняется служба, нужно изменить свойство <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>.</span><span class="sxs-lookup"><span data-stu-id="860e9-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="860e9-109">Это свойство позволяет задать для службы один из четырех типов учетных записей.</span><span class="sxs-lookup"><span data-stu-id="860e9-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="860e9-110">`User`. Система запрашивает действительное имя пользователя и пароль, когда служба устанавливается и запускается в контексте учетной записи, указанной одним пользователем по сети.</span><span class="sxs-lookup"><span data-stu-id="860e9-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="860e9-111">`LocalService`. Выполняется в контексте учетной записи, которая аналогична учетной записи непривилегированного пользователя локального компьютера. Удаленным серверам при этом передаются учетные данные анонимного пользователя.</span><span class="sxs-lookup"><span data-stu-id="860e9-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="860e9-112">`LocalSystem`. Выполняется в контексте учетной записи, которая предоставляет широкие локальные привилегии. Удаленным серверам при этом передаются учетные данные компьютера.</span><span class="sxs-lookup"><span data-stu-id="860e9-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="860e9-113">`NetworkService`. Выполняется в контексте учетной записи, которая аналогична учетной записи непривилегированного пользователя локального компьютера. Удаленным серверам при этом передаются учетные данные компьютера.</span><span class="sxs-lookup"><span data-stu-id="860e9-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="860e9-114">Дополнительные сведения см. в описании перечисления <xref:System.ServiceProcess.ServiceAccount>.</span><span class="sxs-lookup"><span data-stu-id="860e9-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="860e9-115">Назначение службам контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="860e9-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="860e9-116">Создав службу, добавьте для нее необходимые установщики.</span><span class="sxs-lookup"><span data-stu-id="860e9-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="860e9-117">Дополнительные сведения см. в разделе [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="860e9-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="860e9-118">В конструкторе откройте класс `ProjectInstaller` и щелкните установщик процессов службы, с которой вы работаете.</span><span class="sxs-lookup"><span data-stu-id="860e9-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="860e9-119">В классе `ProjectInstaller` для каждого приложения-службы есть по крайней мере два компонента установки: установщик процессов для всех служб в проекте и установщик для каждой службы приложения.</span><span class="sxs-lookup"><span data-stu-id="860e9-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="860e9-120">Сейчас вам нужно выбрать <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="860e9-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="860e9-121">В окне **Свойства** задайте для свойства <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="860e9-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860e9-122">См. также</span><span class="sxs-lookup"><span data-stu-id="860e9-122">See also</span></span>

- [<span data-ttu-id="860e9-123">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="860e9-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="860e9-124">Практическое руководство. Добавление установщиков в приложение-службу</span><span class="sxs-lookup"><span data-stu-id="860e9-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="860e9-125">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="860e9-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
