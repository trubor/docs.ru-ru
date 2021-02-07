---
description: 'Дополнительные сведения: олицетворение и возврат'
title: Олицетворение и возвращение
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: f3e536f87ef5aa09cd727fe9674c7a40f3a09150
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685014"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="c623b-103">Олицетворение и возвращение</span><span class="sxs-lookup"><span data-stu-id="c623b-103">Impersonating and Reverting</span></span>

> [!NOTE]
> <span data-ttu-id="c623b-104">Эта статья относится к Windows.</span><span class="sxs-lookup"><span data-stu-id="c623b-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="c623b-105">Сведения о ASP.NET Core см. в разделе [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="c623b-105">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="c623b-106">Иногда может потребоваться получить токен учетной записи Windows для олицетворения учетной записи Windows.</span><span class="sxs-lookup"><span data-stu-id="c623b-106">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="c623b-107">Например, приложению ASP.NET может требоваться действовать от лица разных пользователей в разное время.</span><span class="sxs-lookup"><span data-stu-id="c623b-107">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="c623b-108">Ваше приложение может принять токен, представляющий администратора, из служб IIS, выполнить олицетворение этого пользователя, выполнить операцию и вернуться к предыдущему удостоверению.</span><span class="sxs-lookup"><span data-stu-id="c623b-108">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="c623b-109">Далее он может принять токен из служб IIS, который представляет пользователя с меньшим набором прав, выполнить некую операцию и снова вернуться.</span><span class="sxs-lookup"><span data-stu-id="c623b-109">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="c623b-110">В ситуациях, когда приложение должно олицетворять учетную запись Windows, не подключенную к текущему потоку службами IIS, необходимо получить токен для этой учетной записи и с его помощью активировать эту учетную запись.</span><span class="sxs-lookup"><span data-stu-id="c623b-110">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="c623b-111">Это можно сделать, выполнив следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="c623b-111">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="c623b-112">Получите токен учетной записи для конкретного пользователя путем вызова неуправляемого метода **LogonUser**.</span><span class="sxs-lookup"><span data-stu-id="c623b-112">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="c623b-113">Этот метод отсутствует в библиотеке базовых классов .NET, но находится в неуправляемой **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="c623b-113">This method is not in the .NET base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="c623b-114">Доступ к методам в неуправляемом коде является сложной операцией и выходит за рамки данного обсуждения.</span><span class="sxs-lookup"><span data-stu-id="c623b-114">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="c623b-115">Дополнительные сведения см. в разделе [Взаимодействие с неуправляемым кодом](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="c623b-115">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="c623b-116">Дополнительные сведения о методе **LogonUser** и библиотеке **advapi32.dll** см. в документации Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="c623b-116">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="c623b-117">Создайте новый экземпляр класса **WindowsIdentity**, передав токен.</span><span class="sxs-lookup"><span data-stu-id="c623b-117">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="c623b-118">Следующий код демонстрирует этот вызов, где `hToken` представляет токен Windows.</span><span class="sxs-lookup"><span data-stu-id="c623b-118">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="c623b-119">Начните олицетворение, создав новый экземпляр класса <xref:System.Security.Principal.WindowsImpersonationContext> и инициализировав его с помощью метода <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> инициализации класса, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="c623b-119">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="c623b-120">Если это олицетворение больше не требуется, вызовите метод <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> для отмены олицетворения, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="c623b-120">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="c623b-121">Если доверенный код уже подключил <xref:System.Security.Principal.WindowsPrincipal> объект к потоку, можно вызвать метод экземпляра **impersonate**, который не принимает маркер учетной записи.</span><span class="sxs-lookup"><span data-stu-id="c623b-121">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="c623b-122">Обратите внимание, что это целесообразно только в том случае, если объект **WindowsPrincipal** в потоке представляет пользователя, отличного от того, под которым выполняется процесс.</span><span class="sxs-lookup"><span data-stu-id="c623b-122">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="c623b-123">Например, такая ситуация может возникнуть при использовании ASP.NET с включенной проверкой подлинности Windows и отключенным олицетворением.</span><span class="sxs-lookup"><span data-stu-id="c623b-123">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="c623b-124">В этом случае процесс выполняется под учетной записью, настроенной в IIS, тогда как текущий участник представляет пользователя Windows, который обращается к странице.</span><span class="sxs-lookup"><span data-stu-id="c623b-124">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="c623b-125">Обратите внимание, что ни **олицетворение** , ни **Отмена** изменений не изменяет объект **Principal** ( <xref:System.Security.Principal.IPrincipal> ), связанный с текущим контекстом вызова.</span><span class="sxs-lookup"><span data-stu-id="c623b-125">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="c623b-126">Вместо этого при олицетворении и возврате изменяется маркер, связанный с текущим процессом операционной системы.</span><span class="sxs-lookup"><span data-stu-id="c623b-126">Rather, impersonation and reverting change the token associated with the current operating system process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c623b-127">См. также</span><span class="sxs-lookup"><span data-stu-id="c623b-127">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="c623b-128">Объекты Principal и Identity</span><span class="sxs-lookup"><span data-stu-id="c623b-128">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="c623b-129">Взаимодействие с неуправляемым кодом</span><span class="sxs-lookup"><span data-stu-id="c623b-129">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
- [<span data-ttu-id="c623b-130">Безопасность ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c623b-130">ASP.NET Core Security</span></span>](/aspnet/core/security/)
