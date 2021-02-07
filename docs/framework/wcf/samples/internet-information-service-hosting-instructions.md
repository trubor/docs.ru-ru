---
description: 'Дополнительные сведения: инструкции по размещению службы IIS'
title: Инструкции по размещению в службах IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 51f5230ecbb8eaf4a909c5c09366680b8c555165
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726381"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="20388-103">Инструкции по размещению в службах IIS</span><span class="sxs-lookup"><span data-stu-id="20388-103">Internet Information Service Hosting Instructions</span></span>

<span data-ttu-id="20388-104">Для выполнения примеров, размещаемых в службах IIS, следует убедиться, что службы IIS правильно установлены и запущены.</span><span class="sxs-lookup"><span data-stu-id="20388-104">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="20388-105">Установка служб IIS версии 7.5 в Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="20388-105">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="20388-106">В **Диспетчер сервера** выберите **роли.**</span><span class="sxs-lookup"><span data-stu-id="20388-106">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="20388-107">В разделе **Сводка по ролям** щелкните **Добавить роли**.</span><span class="sxs-lookup"><span data-stu-id="20388-107">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="20388-108">Нажмите кнопку **Далее** , чтобы открыть диалоговое окно **Выбор ролей сервера** .</span><span class="sxs-lookup"><span data-stu-id="20388-108">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="20388-109">Выберите **сервер приложений** в списке **роли** , а затем дважды нажмите кнопку **Далее** , чтобы открыть диалоговое окно **Выбор служб ролей** для роли сервера приложений.</span><span class="sxs-lookup"><span data-stu-id="20388-109">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="20388-110">Установите флажок **веб-сервер (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="20388-110">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="20388-111">Если будет предложено установить дополнительные службы ролей и компоненты, щелкните **Добавить необходимые компоненты**.</span><span class="sxs-lookup"><span data-stu-id="20388-111">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="20388-112">Дважды нажмите кнопку **Далее** , чтобы отобразить диалоговое окно **Выбор служб ролей** для роли веб-сервера (IIS).</span><span class="sxs-lookup"><span data-stu-id="20388-112">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="20388-113">Разверните узел **средства управления**, а затем узел **Совместимость управления IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-113">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="20388-114">Выберите пункт **средства работы со скриптами IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-114">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="20388-115">Если будет предложено установить дополнительные службы ролей и компоненты, щелкните **Добавить необходимые службы ролей**.</span><span class="sxs-lookup"><span data-stu-id="20388-115">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="20388-116">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-116">Click **Next**.</span></span>  
  
6. <span data-ttu-id="20388-117">Если сводка выбора правильная, нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="20388-117">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="20388-118">После завершения установки нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="20388-118">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="20388-119">Установка служб IIS версии 7.5 в Windows 7</span><span class="sxs-lookup"><span data-stu-id="20388-119">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="20388-120">Нажмите кнопку **Пуск** и выберите **Панель управления**.</span><span class="sxs-lookup"><span data-stu-id="20388-120">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="20388-121">Откройте группу **программы** .</span><span class="sxs-lookup"><span data-stu-id="20388-121">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="20388-122">В разделе **программы и компоненты** щелкните **Включение или отключение компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="20388-122">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="20388-123">Откроется диалоговое окно **контроль учетных записей пользователей** .</span><span class="sxs-lookup"><span data-stu-id="20388-123">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="20388-124">Нажмите кнопку **Continue**(Продолжить).</span><span class="sxs-lookup"><span data-stu-id="20388-124">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="20388-125">Откроется диалоговое окно **компоненты Windows** .</span><span class="sxs-lookup"><span data-stu-id="20388-125">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="20388-126">Разверните элемент с меткой **службы IIS**.</span><span class="sxs-lookup"><span data-stu-id="20388-126">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="20388-127">Разверните элемент, помеченный как **службы** Интернета.</span><span class="sxs-lookup"><span data-stu-id="20388-127">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="20388-128">Разверните элемент **Компоненты разработки приложений**.</span><span class="sxs-lookup"><span data-stu-id="20388-128">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="20388-129">Убедитесь, что выбраны следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="20388-129">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="20388-130">**Расширяемость платформы .NET**</span><span class="sxs-lookup"><span data-stu-id="20388-130">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="20388-131">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="20388-131">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="20388-132">**Расширения ISAPI**</span><span class="sxs-lookup"><span data-stu-id="20388-132">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="20388-133">**Фильтры ISAPI**</span><span class="sxs-lookup"><span data-stu-id="20388-133">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="20388-134">В элементе **веб-службы в Интернете** разверните узел **Общие функции HTTP**.</span><span class="sxs-lookup"><span data-stu-id="20388-134">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="20388-135">Убедитесь, что выбрано **статическое содержимое** .</span><span class="sxs-lookup"><span data-stu-id="20388-135">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="20388-136">Под элементом **веб-службы в Интернете** разверните узел **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="20388-136">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="20388-137">Убедитесь, что выбрана **Проверка подлинности Windows** .</span><span class="sxs-lookup"><span data-stu-id="20388-137">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="20388-138">В каталоге **службы IIS** разверните элемент **средства управления веб-** узлом, а затем выберите **консоль управления IIS**.</span><span class="sxs-lookup"><span data-stu-id="20388-138">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="20388-139">Разверните элемент с меткой **Совместимость управления IIS 6**, а затем выберите пункт **средства создания скриптов IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-139">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="20388-140">В каталоге **службы IIS** разверните элемент **Microsoft .NET Framework 3.5.1**, а затем выберите **Windows Communication Foundation HTTP Activation**.</span><span class="sxs-lookup"><span data-stu-id="20388-140">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="20388-141">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="20388-141">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="20388-142">Установка служб IIS версии 7.0 в Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="20388-142">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="20388-143">В **Диспетчер сервера** выберите **роли**.</span><span class="sxs-lookup"><span data-stu-id="20388-143">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="20388-144">В разделе **Сводка по ролям** щелкните **Добавить роли**.</span><span class="sxs-lookup"><span data-stu-id="20388-144">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="20388-145">Нажмите кнопку **Далее** , чтобы открыть диалоговое окно **Выбор ролей сервера** .</span><span class="sxs-lookup"><span data-stu-id="20388-145">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="20388-146">Выберите **сервер приложений** в списке **роли** , а затем дважды нажмите кнопку **Далее** , чтобы открыть диалоговое окно **Выбор служб ролей** для роли сервера приложений.</span><span class="sxs-lookup"><span data-stu-id="20388-146">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="20388-147">Установите флажок **веб-сервер (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="20388-147">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="20388-148">Если будет предложено установить дополнительные службы ролей и компоненты, щелкните **Добавить необходимые компоненты**.</span><span class="sxs-lookup"><span data-stu-id="20388-148">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="20388-149">Дважды нажмите кнопку **Далее** , чтобы отобразить диалоговое окно **Выбор служб ролей** для роли веб-сервера (IIS).</span><span class="sxs-lookup"><span data-stu-id="20388-149">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="20388-150">Разверните узел **средства управления**, а затем узел **Совместимость управления IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-150">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="20388-151">Выберите пункт **средства работы со скриптами IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-151">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="20388-152">Если будет предложено установить дополнительные службы ролей и компоненты, щелкните **Добавить необходимые службы ролей**.</span><span class="sxs-lookup"><span data-stu-id="20388-152">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="20388-153">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-153">Click **Next**.</span></span>  
  
6. <span data-ttu-id="20388-154">Если сводка выбора правильная, нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="20388-154">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="20388-155">После завершения установки нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="20388-155">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="20388-156">Установка служб IIS версии 7.0 в Windows Vista</span><span class="sxs-lookup"><span data-stu-id="20388-156">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="20388-157">Нажмите кнопку Пуск, а затем щелкните «Панель управления».</span><span class="sxs-lookup"><span data-stu-id="20388-157">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="20388-158">Выберите группу **программы** .</span><span class="sxs-lookup"><span data-stu-id="20388-158">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="20388-159">В разделе **программы и компоненты** щелкните **Включение или отключение компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="20388-159">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="20388-160">Откроется диалоговое окно **контроль учетных записей пользователей** .</span><span class="sxs-lookup"><span data-stu-id="20388-160">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="20388-161">Нажмите кнопку **Continue**(Продолжить).</span><span class="sxs-lookup"><span data-stu-id="20388-161">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="20388-162">Откроется диалоговое окно **компоненты Windows** .</span><span class="sxs-lookup"><span data-stu-id="20388-162">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="20388-163">Разверните элемент с меткой **службы IIS**.</span><span class="sxs-lookup"><span data-stu-id="20388-163">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="20388-164">Разверните элемент, помеченный как **службы** Интернета.</span><span class="sxs-lookup"><span data-stu-id="20388-164">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="20388-165">Разверните элемент **Компоненты разработки приложений**.</span><span class="sxs-lookup"><span data-stu-id="20388-165">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="20388-166">Убедитесь, что выбраны следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="20388-166">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="20388-167">**Расширяемость платформы .NET**</span><span class="sxs-lookup"><span data-stu-id="20388-167">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="20388-168">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="20388-168">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="20388-169">**Расширения ISAPI**</span><span class="sxs-lookup"><span data-stu-id="20388-169">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="20388-170">**Фильтры ISAPI**</span><span class="sxs-lookup"><span data-stu-id="20388-170">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="20388-171">Разверните элемент **средства управления веб-сайтами**, а затем выберите **консоль управления IIS**.</span><span class="sxs-lookup"><span data-stu-id="20388-171">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="20388-172">В элементе **веб-службы в Интернете** разверните узел **Общие функции HTTP**.</span><span class="sxs-lookup"><span data-stu-id="20388-172">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="20388-173">Убедитесь, что выбрано **статическое содержимое** .</span><span class="sxs-lookup"><span data-stu-id="20388-173">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="20388-174">Под элементом **веб-службы в Интернете** разверните узел **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="20388-174">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="20388-175">Убедитесь, что выбрана **Проверка подлинности Windows** .</span><span class="sxs-lookup"><span data-stu-id="20388-175">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="20388-176">Разверните элемент с меткой **Совместимость управления IIS 6**, а затем выберите пункт **средства создания скриптов IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="20388-176">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="20388-177">Разверните элемент, помеченный **Microsoft .NET Framework 3,0**, а затем выберите **Windows Communication Foundation HTTP Activation**.</span><span class="sxs-lookup"><span data-stu-id="20388-177">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="20388-178">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="20388-178">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="20388-179">Установка служб IIS версии 6.0 в Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="20388-179">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="20388-180">В меню **Управление сервером** выберите команду **Добавить или удалить роль**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-180">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="20388-181">Выберите **сервер приложений (IIS, ASP.NET)** в списке **роль сервера** , а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-181">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="20388-182">Установите флажок **включить ASP.NET** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-182">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="20388-183">Если элементы выбраны правильно, нажмите кнопку Далее.</span><span class="sxs-lookup"><span data-stu-id="20388-183">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="20388-184">Установка служб IIS версии 5.1 в Windows XP с установленными пакетами обновления 2 и 3 (SP2 и SP3)</span><span class="sxs-lookup"><span data-stu-id="20388-184">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="20388-185">На панели управления выберите **Установка и удаление программ**.</span><span class="sxs-lookup"><span data-stu-id="20388-185">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="20388-186">Нажмите в диалоговом окне **Установка и удаление программ** кнопку **Установка компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="20388-186">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="20388-187">В **мастере компонентов Windows** установите флажок **службы IIS (IIS)** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="20388-187">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="20388-188">Если появится диалоговое окно **необходимые файлы** , вставьте установочный диск операционной системы, перейдите в папку i386 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="20388-188">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="20388-189">После завершения установки нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="20388-189">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="20388-190">Закройте диалоговое окно **Установка и удаление программ** и закройте **Панель управления**.</span><span class="sxs-lookup"><span data-stu-id="20388-190">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="20388-191">Проверка установки служб IIS и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20388-191">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="20388-192">Сохраните HTML-файл, указанный в конце данного раздела, в корневом каталоге \InetPub\wwwroot и назовите его Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="20388-192">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="20388-193">Откройте окно браузера.</span><span class="sxs-lookup"><span data-stu-id="20388-193">Open a browser window.</span></span>  
  
3. <span data-ttu-id="20388-194">Введите `http://localhost/Default.aspx` в поле адрес и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="20388-194">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="20388-195">Должна появиться веб-страница с текстом "Здравствуй, мир!".</span><span class="sxs-lookup"><span data-stu-id="20388-195">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20388-196">Каждый раз при установке новой версии платформа .NET Framework необходимо повторно зарегистрировать aspnet_isapi как расширение веб-службы для IIS.</span><span class="sxs-lookup"><span data-stu-id="20388-196">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="20388-197">Чтобы сделать это, выполните команду `aspnet_regiis –I –enable`.</span><span class="sxs-lookup"><span data-stu-id="20388-197">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="20388-198">Пример кода</span><span class="sxs-lookup"><span data-stu-id="20388-198">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
