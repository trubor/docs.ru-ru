---
title: Certmgr.exe (средство диспетчера сертификатов)
description: См. сведения о Certmgr.exe, инструменте диспетчера сертификатов. Этот инструмент управляет сертификатами, списками доверенных сертификатов и списками отзыва сертификатов.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: eba8253a52f9dc533848fc7cbb76566c726495a2
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654197"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="72824-104">Certmgr.exe (средство диспетчера сертификатов)</span><span class="sxs-lookup"><span data-stu-id="72824-104">Certmgr.exe (Certificate Manager Tool)</span></span>

<span data-ttu-id="72824-105">Диспетчер сертификатов (Certmgr.exe) предназначен для управления сертификатами, списками доверия сертификатов (CTL) и списками отзыва сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="72824-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="72824-106">Диспетчер сертификатов устанавливается автоматически вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72824-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="72824-107">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="72824-107">To start the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72824-108">Диспетчер сертификатов (Certmgr.exe) является служебной программой командной строки, в то время как сертификаты (Certmgr.msc) — это оснастка консоли управления (MMC).</span><span class="sxs-lookup"><span data-stu-id="72824-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="72824-109">Поскольку файл Certmgr.msc обычно находится в системном каталоге Windows, при вводе `certmgr` в командной строке может загрузиться оснастка консоли управления (MMC) "Сертификаты", даже если открыта командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72824-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="72824-110">Это происходит потому, что путь к оснастке предшествует пути к диспетчеру сертификатов в переменной среды PATH.</span><span class="sxs-lookup"><span data-stu-id="72824-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="72824-111">При возникновении этой проблемы команды Certmgr.exe можно выполнить, указав путь к исполняемому файлу.</span><span class="sxs-lookup"><span data-stu-id="72824-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>
  
 <span data-ttu-id="72824-112">Общие сведения о сертификатах X.509 см. в разделе [Работа с сертификатами](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="72824-112">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="72824-113">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="72824-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72824-114">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72824-114">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="72824-115">Параметры</span><span class="sxs-lookup"><span data-stu-id="72824-115">Parameters</span></span>  
  
|<span data-ttu-id="72824-116">Аргумент</span><span class="sxs-lookup"><span data-stu-id="72824-116">Argument</span></span>|<span data-ttu-id="72824-117">Описание</span><span class="sxs-lookup"><span data-stu-id="72824-117">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="72824-118">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="72824-118">*sourceStorename*</span></span>|<span data-ttu-id="72824-119">Хранилище сертификатов, содержащее существующие сертификаты, списки доверия сертификатов (CTL) и списки отзыва сертификатов (CRL) для добавления, удаления, сохранения или отображения.</span><span class="sxs-lookup"><span data-stu-id="72824-119">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="72824-120">Это может быть файл хранилища или хранилище систем.</span><span class="sxs-lookup"><span data-stu-id="72824-120">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="72824-121">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="72824-121">*destinationStorename*</span></span>|<span data-ttu-id="72824-122">Конечное хранилище сертификатов или файл.</span><span class="sxs-lookup"><span data-stu-id="72824-122">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="72824-123">Параметр</span><span class="sxs-lookup"><span data-stu-id="72824-123">Option</span></span>|<span data-ttu-id="72824-124">Описание:</span><span class="sxs-lookup"><span data-stu-id="72824-124">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="72824-125">**/add**</span><span class="sxs-lookup"><span data-stu-id="72824-125">**/add**</span></span>|<span data-ttu-id="72824-126">Добавляет сертификаты, CTL и CRL в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-126">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="72824-127">**/all**</span><span class="sxs-lookup"><span data-stu-id="72824-127">**/all**</span></span>|<span data-ttu-id="72824-128">Добавляет все записи при использовании параметра **/add**.</span><span class="sxs-lookup"><span data-stu-id="72824-128">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="72824-129">Удаляет все записи при использовании параметра **/del**. Отображает все записи при использовании без параметров **/add** или **/del**.</span><span class="sxs-lookup"><span data-stu-id="72824-129">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="72824-130">Параметр **/all** нельзя использовать вместе с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-130">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="72824-131">**/c**</span><span class="sxs-lookup"><span data-stu-id="72824-131">**/c**</span></span>|<span data-ttu-id="72824-132">Добавляет сертификаты при использовании параметра **/add**.</span><span class="sxs-lookup"><span data-stu-id="72824-132">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="72824-133">Удаляет сертификаты при использовании параметра **/del**. Сохраняет сертификаты при использовании параметра **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-133">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="72824-134">Отображает сертификаты при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-134">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="72824-135">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="72824-135">**/CRL**</span></span>|<span data-ttu-id="72824-136">При использовании с параметром **/add** добавляет списки отзыва сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="72824-136">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="72824-137">При использовании с параметром **/del** удаляет списки отзыва сертификатов (CRL). Сохраняет списки CRL при использовании с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-137">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="72824-138">Отображает списки отзыва сертификатов (CRL) при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-138">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="72824-139">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="72824-139">**/CTL**</span></span>|<span data-ttu-id="72824-140">При использовании с параметром **/add** добавляет списки доверия сертификатов (CTL).</span><span class="sxs-lookup"><span data-stu-id="72824-140">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="72824-141">При использовании с параметром **/del** удаляет списки доверия сертификатов (CTL). Сохраняет списки CTL при использовании с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-141">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="72824-142">Отображает списки доверия сертификатов (CTL) при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-142">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="72824-143">**/del**</span><span class="sxs-lookup"><span data-stu-id="72824-143">**/del**</span></span>|<span data-ttu-id="72824-144">Удаляет сертификаты, CTL и CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-144">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="72824-145">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="72824-145">**/e** *encodingType*</span></span>|<span data-ttu-id="72824-146">Указывает тип шифрования сертификата.</span><span class="sxs-lookup"><span data-stu-id="72824-146">Specifies the certificate encoding type.</span></span> <span data-ttu-id="72824-147">Значение по умолчанию — `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="72824-147">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="72824-148">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="72824-148">**/f** *dwFlags*</span></span>|<span data-ttu-id="72824-149">Задает открытый флаг хранилища.</span><span class="sxs-lookup"><span data-stu-id="72824-149">Specifies the store open flag.</span></span> <span data-ttu-id="72824-150">Это параметр *dwFlags*, передаваемый методу **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="72824-150">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="72824-151">По умолчанию используется значение CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="72824-151">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="72824-152">Этот параметр обрабатывается, только если задан параметр **/y**.</span><span class="sxs-lookup"><span data-stu-id="72824-152">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="72824-153">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="72824-153">**/h**[**elp**]</span></span>|<span data-ttu-id="72824-154">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="72824-154">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="72824-155">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="72824-155">**/n** *nam*</span></span>|<span data-ttu-id="72824-156">Задает общее имя добавляемого, удаляемого или сохраняемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="72824-156">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="72824-157">Этот параметр может применяться только для сертификатов, его нельзя задавать для CTL и CRL.</span><span class="sxs-lookup"><span data-stu-id="72824-157">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="72824-158">**/put**</span><span class="sxs-lookup"><span data-stu-id="72824-158">**/put**</span></span>|<span data-ttu-id="72824-159">Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-159">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="72824-160">Файл сохраняется в формате X.509.</span><span class="sxs-lookup"><span data-stu-id="72824-160">The file is saved in X.509 format.</span></span> <span data-ttu-id="72824-161">Чтобы сохранить файл в формате PKCS #7, можно использовать параметр **/7** с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-161">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="72824-162">За параметром **/put** должен следовать параметр **/c**, **/CTL** или **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="72824-162">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="72824-163">Параметр **/all** нельзя использовать вместе с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-163">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="72824-164">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="72824-164">**/r** *location*</span></span>|<span data-ttu-id="72824-165">Указывает расположение системного хранилища в реестре.</span><span class="sxs-lookup"><span data-stu-id="72824-165">Identifies the registry location of the system store.</span></span> <span data-ttu-id="72824-166">Этот параметр обрабатывается, только если задан параметр **/s**.</span><span class="sxs-lookup"><span data-stu-id="72824-166">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="72824-167">Параметр *location* должен иметь одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="72824-167">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="72824-168">-   `currentUser` означает, что хранилище сертификатов находится в разделе HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="72824-168">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="72824-169">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="72824-169">This is the default.</span></span><br /><span data-ttu-id="72824-170">-   `localMachine` означает, что хранилище сертификатов находится в разделе HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="72824-170">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="72824-171">**/s**</span><span class="sxs-lookup"><span data-stu-id="72824-171">**/s**</span></span>|<span data-ttu-id="72824-172">Означает, что хранилище сертификатов является системным.</span><span class="sxs-lookup"><span data-stu-id="72824-172">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="72824-173">Если этот параметр не задан, хранилищем считается **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="72824-173">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="72824-174">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="72824-174">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="72824-175">Задает хэш SHA1 добавляемого, удаляемого или сохраняемого сертификата, CTL или CRL.</span><span class="sxs-lookup"><span data-stu-id="72824-175">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="72824-176">**/v**</span><span class="sxs-lookup"><span data-stu-id="72824-176">**/v**</span></span>|<span data-ttu-id="72824-177">Включает отображение подробных сведений о сертификатах, CTL и CRL.</span><span class="sxs-lookup"><span data-stu-id="72824-177">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="72824-178">Этот параметр невозможно использовать с параметрами **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="72824-178">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="72824-179">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="72824-179">**/y** *provider*</span></span>|<span data-ttu-id="72824-180">Задает имя поставщика хранилища.</span><span class="sxs-lookup"><span data-stu-id="72824-180">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="72824-181">**/7**</span><span class="sxs-lookup"><span data-stu-id="72824-181">**/7**</span></span>|<span data-ttu-id="72824-182">Сохраняет конечное хранилище как объект PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="72824-182">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="72824-183">**/?**</span><span class="sxs-lookup"><span data-stu-id="72824-183">**/?**</span></span>|<span data-ttu-id="72824-184">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="72824-184">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72824-185">Примечания</span><span class="sxs-lookup"><span data-stu-id="72824-185">Remarks</span></span>  

 <span data-ttu-id="72824-186">Основные функции программы Certmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="72824-186">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="72824-187">Отображение сведений о сертификатах, CTL и CRL на консоли.</span><span class="sxs-lookup"><span data-stu-id="72824-187">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="72824-188">Добавляет сертификаты, CTL и CRL в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-188">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="72824-189">Удаляет сертификаты, CTL и CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-189">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="72824-190">Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-190">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="72824-191">Программа Certmgr.exe работает с двумя типами хранилищ сертификатов: системным и **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="72824-191">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="72824-192">Указывать тип хранилища необязательно, поскольку программа Cedrtmgr.exe может автоматически определить тип хранилища и выполнить соответствующие действия.</span><span class="sxs-lookup"><span data-stu-id="72824-192">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="72824-193">При запуске программы Certmgr.exe без параметров выполняется оснастка "certmgr.msc" с графическим интерфейсом пользователя, облегчающим управление сертификатами, что также можно сделать из командной строки.</span><span class="sxs-lookup"><span data-stu-id="72824-193">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="72824-194">В графическом интерфейсе пользователя имеется мастер импорта, копирующий сертификаты, CTL и CRL с диска в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-194">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="72824-195">Чтобы найти имена хранилищ X509Certificate для параметров `sourceStorename` и `destinationStorename`, можно скомпилировать и выполнить следующий код.</span><span class="sxs-lookup"><span data-stu-id="72824-195">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="72824-196">Дополнительные сведения см. в разделе [Работа с сертификатами](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="72824-196">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="72824-197">Примеры</span><span class="sxs-lookup"><span data-stu-id="72824-197">Examples</span></span>  

 <span data-ttu-id="72824-198">Следующая команда выводит подробные сведения о содержимом системного хранилища `my`, используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="72824-198">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="72824-199">Следующая команда добавляет все сертификаты из файла `myFile.ext` в новый файл `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="72824-199">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="72824-200">Следующая команда добавляет сертификат в файле `testcert.cer` в хранилище системы `my`.</span><span class="sxs-lookup"><span data-stu-id="72824-200">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="72824-201">Следующая команда добавляет сертификат в файле `TrustedCert.cer` в хранилище корневых сертификатов.</span><span class="sxs-lookup"><span data-stu-id="72824-201">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="72824-202">Следующая команда сохраняет сертификат с общим именем `myCert` в системном хранилище `my` в файл `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="72824-202">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="72824-203">Следующая команда удаляет все CTL из системного хранилища `my` и сохраняет полученное хранилище в файл `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="72824-203">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="72824-204">Следующая команда сохраняет сертификат в системном хранилище `my` в файл `newFile`.</span><span class="sxs-lookup"><span data-stu-id="72824-204">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="72824-205">Программа запросит у пользователя номер сертификата из хранилища `my`, который следует поместить в файл `newFile`.</span><span class="sxs-lookup"><span data-stu-id="72824-205">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="72824-206">См. также</span><span class="sxs-lookup"><span data-stu-id="72824-206">See also</span></span>

- [<span data-ttu-id="72824-207">Инструменты</span><span class="sxs-lookup"><span data-stu-id="72824-207">Tools</span></span>](index.md)
- [<span data-ttu-id="72824-208">Makecert.exe (средство создания сертификатов)</span><span class="sxs-lookup"><span data-stu-id="72824-208">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="72824-209">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="72824-209">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
