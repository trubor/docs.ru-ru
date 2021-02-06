---
description: Дополнительные сведения см. в статье Использование средств разработки WCF.
title: Использование средств разработки WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: c96644fb66006447f6a05f6c08ea84fe2ed99ce8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631701"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="cc3f9-103">Использование средств разработки WCF</span><span class="sxs-lookup"><span data-stu-id="cc3f9-103">Using the WCF Development Tools</span></span>

<span data-ttu-id="cc3f9-104">В этом разделе описываются средства разработки Visual Studio, которые помогут вам в разработке WCFservice.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-104">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="cc3f9-105">Вы можете использовать шаблоны Visual Studio в качестве основы для быстрого создания собственной службы, а затем для отладки и тестирования службы использовать автоматическое размещение службы WCF и клиент тестов WCF.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-105">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="cc3f9-106">Оба этих инструмента обеспечивают быстрый и удобный цикл отладки и тестирования и исключают необходимость фиксации модели размещения на ранней стадии.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-106">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="cc3f9-107">Начиная с Visual Studio 2017 средства разработки WCF по умолчанию не устанавливаются.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-107">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="cc3f9-108">Чтобы использовать эти функции, необходимо убедиться в том, что в установщике Visual Studio выбран компонент Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-108">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="cc3f9-109">Инструменты разработчика WCF</span><span class="sxs-lookup"><span data-stu-id="cc3f9-109">The WCF Developer Tools</span></span>  

 [<span data-ttu-id="cc3f9-110">Шаблоны WCF в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cc3f9-110">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="cc3f9-111">Вы можете использовать стандартные шаблоны проектов и элементов Visual Studio в Visual Studio для быстрой сборки служб WCF и окружающих приложений.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-111">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="cc3f9-112">Узел службы WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cc3f9-112">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="cc3f9-113">Автоматическое размещение службы WCF (WcfSvcHost.exe) позволяет запустить отладчик Visual Studio (F5) для автоматического размещения и тестирования реализованной службы.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-113">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="cc3f9-114">Затем можно протестировать службу с помощью тестового клиента WCF (wcfTestClient.exe) или собственного клиента, чтобы найти и исправить возможные ошибки.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-114">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="cc3f9-115">Тестовый клиент WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="cc3f9-115">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="cc3f9-116">Тестовый клиент WCF (WcfTestClient.exe) — это средство графического пользовательского интерфейса, которое позволяет вводить параметры произвольных типов, отправлять эти входные данные в службу и просматривать ответ, отправляемый службой обратно.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-116">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="cc3f9-117">Она обеспечивает простой процесс тестирования служб при объединении с автоматическим размещением службы WCF.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-117">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="cc3f9-118">Формирование классов типов данных из XML</span><span class="sxs-lookup"><span data-stu-id="cc3f9-118">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="cc3f9-119">Данные XML, сохраненные в буфере обмена, можно вставить в кодовую страницу.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-119">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="cc3f9-120">Классы, определенные в данных, будут преобразованы в типы кода.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-120">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="cc3f9-121">Использование инструментов без прав администратора</span><span class="sxs-lookup"><span data-stu-id="cc3f9-121">Using the Tools without Administrator privilege</span></span>  

 <span data-ttu-id="cc3f9-122">Чтобы разрешить пользователям без прав администратора для разработки служб WCF, в процессе установки Visual Studio создается список управления доступом (ACL) для пространства имен " http://+:8731/Design_Time_Addresses ".</span><span class="sxs-lookup"><span data-stu-id="cc3f9-122">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="cc3f9-123">Список управления доступом определяется пользовательским интерфейсом, который включает всех пользователей, выполнивших вход в систему.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-123">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="cc3f9-124">Администраторы могут добавлять или удалять пользователей из этого списка ACL или открыть дополнительные порты. Этот список ACL позволяет шаблонам WCF или WF отправлять и получать данные в их конфигурации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-124">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="cc3f9-125">Он также позволяет пользователям использовать автоматическое размещение службы WCF (wcfSvcHost.exe) без предоставления прав администратора.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-125">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="cc3f9-126">Вы можете изменить доступ с помощью средства Netsh.exe в Windows Vista в учетной записи администратора с повышенными правами.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-126">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="cc3f9-127">Ниже приведен пример использования средства Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="cc3f9-127">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="cc3f9-128">Дополнительные сведения о Netsh.exe см. в разделе [Использование средства Netsh.exe и параметров Command-Line](/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="cc3f9-128">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3f9-129">См. также</span><span class="sxs-lookup"><span data-stu-id="cc3f9-129">See also</span></span>

- [<span data-ttu-id="cc3f9-130">Шаблоны WCF в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cc3f9-130">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="cc3f9-131">Узел службы WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cc3f9-131">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="cc3f9-132">Тестовый клиент WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="cc3f9-132">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
