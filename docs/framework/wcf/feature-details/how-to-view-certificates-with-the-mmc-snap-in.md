---
title: Пошаговое руководство. Просмотр сертификатов с помощью оснастки MMC
description: Безопасный клиент или служба WCF могут использовать сертификат в качестве учетных данных. Сведения о типах хранилищ сертификатов, которые можно проверить с помощью подключаемого модуля MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 788161db2e38dc942b0c638128f8599b0436c8fd
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604584"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="47a5f-104">Пошаговое руководство. Просмотр сертификатов с помощью оснастки MMC</span><span class="sxs-lookup"><span data-stu-id="47a5f-104">How to: View certificates with the MMC snap-in</span></span>

<span data-ttu-id="47a5f-105">При создании защищенного клиента или службы можно использовать [сертификат](working-with-certificates.md) в качестве учетных данных.</span><span class="sxs-lookup"><span data-stu-id="47a5f-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="47a5f-106">Например, общий тип учетных данных — это сертификат X. 509, который создается с помощью <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="47a5f-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="47a5f-107">Существует три разных типа хранилищ сертификатов, которые можно проверить с помощью консоли управления (MMC) в системах Windows:</span><span class="sxs-lookup"><span data-stu-id="47a5f-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="47a5f-108">Локальный компьютер. хранилище является локальным для устройства и является глобальным для всех пользователей на устройстве.</span><span class="sxs-lookup"><span data-stu-id="47a5f-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="47a5f-109">Текущий пользователь: хранилище является локальным по отношению к текущей учетной записи пользователя на устройстве.</span><span class="sxs-lookup"><span data-stu-id="47a5f-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="47a5f-110">Учетная запись службы. хранилище является локальным для определенной службы на устройстве.</span><span class="sxs-lookup"><span data-stu-id="47a5f-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="47a5f-111">Просмотр сертификатов в оснастке MMC</span><span class="sxs-lookup"><span data-stu-id="47a5f-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="47a5f-112">В следующей процедуре показано, как проверить магазины на локальном устройстве, чтобы найти соответствующий сертификат:</span><span class="sxs-lookup"><span data-stu-id="47a5f-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="47a5f-113">В меню **Пуск** выберите пункт **выполнить** и введите *MMC*.</span><span class="sxs-lookup"><span data-stu-id="47a5f-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="47a5f-114">Откроется консоль MMC.</span><span class="sxs-lookup"><span data-stu-id="47a5f-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="47a5f-115">В меню **файл** выберите команду **Добавить или удалить оснастку**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="47a5f-116">Откроется окно **Добавление или удаление оснасток** .</span><span class="sxs-lookup"><span data-stu-id="47a5f-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="47a5f-117">В списке **Доступные оснастки** выберите **Сертификаты**, а затем щелкните **добавить**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Добавить оснастку сертификатов](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="47a5f-119">В окне **оснастки "сертификаты** " выберите **учетная запись компьютера**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="47a5f-120">При необходимости можно выбрать **учетную запись пользователя** для текущего пользователя или **учетной записи службы** для конкретной службы.</span><span class="sxs-lookup"><span data-stu-id="47a5f-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="47a5f-121">Если вы не являетесь администратором устройства, вы можете управлять сертификатами только для учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="47a5f-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="47a5f-122">В окне **Выбор компьютера** оставьте выбранным параметр **локальный компьютер** и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="47a5f-123">В окне **Добавление или удаление оснастки** нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Окно "Добавление и удаление оснасток" с выделенной кнопкой "ОК"](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="47a5f-125">Необязательно. в меню **файл** выберите **сохранить** или **Сохранить как** , чтобы сохранить файл консоли MMC для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="47a5f-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="47a5f-126">Чтобы просмотреть сертификаты в оснастке MMC, выберите **корень консоли** в левой области, а затем разверните узел **Сертификаты (локальный компьютер)**.</span><span class="sxs-lookup"><span data-stu-id="47a5f-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="47a5f-127">Появится список каталогов для каждого типа сертификатов.</span><span class="sxs-lookup"><span data-stu-id="47a5f-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="47a5f-128">Из каждого каталога сертификатов можно просматривать, экспортировать, импортировать и удалять свои сертификаты.</span><span class="sxs-lookup"><span data-stu-id="47a5f-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="47a5f-129">Просмотр сертификатов с помощью средства диспетчера сертификатов</span><span class="sxs-lookup"><span data-stu-id="47a5f-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="47a5f-130">Вы также можете просматривать, экспортировать, импортировать и удалять сертификаты с помощью средства диспетчера сертификатов.</span><span class="sxs-lookup"><span data-stu-id="47a5f-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="47a5f-131">Просмотр сертификатов для локального устройства</span><span class="sxs-lookup"><span data-stu-id="47a5f-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="47a5f-132">В меню **Пуск** выберите пункт **выполнить** , а затем введите *certlm. msc*.</span><span class="sxs-lookup"><span data-stu-id="47a5f-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="47a5f-133">Откроется средство диспетчера сертификатов для локального устройства.</span><span class="sxs-lookup"><span data-stu-id="47a5f-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="47a5f-134">Для просмотра сертификатов в разделе **Сертификаты — локальный компьютер** в левой области разверните каталог для типа сертификата, который нужно просмотреть.</span><span class="sxs-lookup"><span data-stu-id="47a5f-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="47a5f-135">Просмотр сертификатов для текущего пользователя</span><span class="sxs-lookup"><span data-stu-id="47a5f-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="47a5f-136">В меню **Пуск** выберите пункт **выполнить** , а затем введите *CertMgr. msc*.</span><span class="sxs-lookup"><span data-stu-id="47a5f-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="47a5f-137">Появится средство диспетчера сертификатов для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="47a5f-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="47a5f-138">Чтобы просмотреть сертификаты, в разделе **Сертификаты — текущий пользователь** в левой области разверните каталог для типа сертификата, который нужно просмотреть.</span><span class="sxs-lookup"><span data-stu-id="47a5f-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="47a5f-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="47a5f-139">See also</span></span>

- [<span data-ttu-id="47a5f-140">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="47a5f-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="47a5f-141">Как создать временные сертификаты для использования во время разработки</span><span class="sxs-lookup"><span data-stu-id="47a5f-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="47a5f-142">Как получить отпечаток сертификата</span><span class="sxs-lookup"><span data-stu-id="47a5f-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
