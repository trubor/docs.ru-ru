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
ms.openlocfilehash: a5666645c674bbbe77b988fc7a1ff0db935920aa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258238"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="e983d-104">Certmgr.exe (средство диспетчера сертификатов)</span><span class="sxs-lookup"><span data-stu-id="e983d-104">Certmgr.exe (Certificate Manager Tool)</span></span>

<span data-ttu-id="e983d-105">Диспетчер сертификатов (Certmgr.exe) предназначен для управления сертификатами, списками доверия сертификатов (CTL) и списками отзыва сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="e983d-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="e983d-106">Диспетчер сертификатов устанавливается автоматически вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e983d-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e983d-107">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="e983d-107">To start the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e983d-108">Диспетчер сертификатов (Certmgr.exe) является служебной программой командной строки, в то время как сертификаты (Certmgr.msc) — это оснастка консоли управления (MMC).</span><span class="sxs-lookup"><span data-stu-id="e983d-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="e983d-109">Поскольку файл Certmgr.msc обычно находится в системном каталоге Windows, при вводе `certmgr` в командной строке может загрузиться оснастка консоли управления (MMC) "Сертификаты", даже если открыта командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e983d-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="e983d-110">Это происходит потому, что путь к оснастке предшествует пути к диспетчеру сертификатов в переменной среды PATH.</span><span class="sxs-lookup"><span data-stu-id="e983d-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="e983d-111">При возникновении этой проблемы команды Certmgr.exe можно выполнить, указав путь к исполняемому файлу.</span><span class="sxs-lookup"><span data-stu-id="e983d-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="e983d-112">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e983d-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e983d-113">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="e983d-113">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="e983d-114">Общие сведения о сертификатах X.509 см. в разделе [Работа с сертификатами](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e983d-114">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="e983d-115">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="e983d-115">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e983d-116">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e983d-116">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="e983d-117">Параметры</span><span class="sxs-lookup"><span data-stu-id="e983d-117">Parameters</span></span>  
  
|<span data-ttu-id="e983d-118">Аргумент</span><span class="sxs-lookup"><span data-stu-id="e983d-118">Argument</span></span>|<span data-ttu-id="e983d-119">Описание</span><span class="sxs-lookup"><span data-stu-id="e983d-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e983d-120">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="e983d-120">*sourceStorename*</span></span>|<span data-ttu-id="e983d-121">Хранилище сертификатов, содержащее существующие сертификаты, списки доверия сертификатов (CTL) и списки отзыва сертификатов (CRL) для добавления, удаления, сохранения или отображения.</span><span class="sxs-lookup"><span data-stu-id="e983d-121">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="e983d-122">Это может быть файл хранилища или хранилище систем.</span><span class="sxs-lookup"><span data-stu-id="e983d-122">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="e983d-123">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="e983d-123">*destinationStorename*</span></span>|<span data-ttu-id="e983d-124">Конечное хранилище сертификатов или файл.</span><span class="sxs-lookup"><span data-stu-id="e983d-124">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="e983d-125">Параметр</span><span class="sxs-lookup"><span data-stu-id="e983d-125">Option</span></span>|<span data-ttu-id="e983d-126">Описание:</span><span class="sxs-lookup"><span data-stu-id="e983d-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e983d-127">**/add**</span><span class="sxs-lookup"><span data-stu-id="e983d-127">**/add**</span></span>|<span data-ttu-id="e983d-128">Добавляет сертификаты, CTL и CRL в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-128">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="e983d-129">**/all**</span><span class="sxs-lookup"><span data-stu-id="e983d-129">**/all**</span></span>|<span data-ttu-id="e983d-130">Добавляет все записи при использовании параметра **/add**.</span><span class="sxs-lookup"><span data-stu-id="e983d-130">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="e983d-131">Удаляет все записи при использовании параметра **/del**. Отображает все записи при использовании без параметров **/add** или **/del**.</span><span class="sxs-lookup"><span data-stu-id="e983d-131">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="e983d-132">Параметр **/all** нельзя использовать вместе с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-132">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="e983d-133">**/c**</span><span class="sxs-lookup"><span data-stu-id="e983d-133">**/c**</span></span>|<span data-ttu-id="e983d-134">Добавляет сертификаты при использовании параметра **/add**.</span><span class="sxs-lookup"><span data-stu-id="e983d-134">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="e983d-135">Удаляет сертификаты при использовании параметра **/del**. Сохраняет сертификаты при использовании параметра **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-135">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="e983d-136">Отображает сертификаты при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-136">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="e983d-137">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="e983d-137">**/CRL**</span></span>|<span data-ttu-id="e983d-138">При использовании с параметром **/add** добавляет списки отзыва сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="e983d-138">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="e983d-139">При использовании с параметром **/del** удаляет списки отзыва сертификатов (CRL). Сохраняет списки CRL при использовании с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-139">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="e983d-140">Отображает списки отзыва сертификатов (CRL) при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-140">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="e983d-141">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="e983d-141">**/CTL**</span></span>|<span data-ttu-id="e983d-142">При использовании с параметром **/add** добавляет списки доверия сертификатов (CTL).</span><span class="sxs-lookup"><span data-stu-id="e983d-142">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="e983d-143">При использовании с параметром **/del** удаляет списки доверия сертификатов (CTL). Сохраняет списки CTL при использовании с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-143">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="e983d-144">Отображает списки доверия сертификатов (CTL) при использовании без параметра **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-144">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="e983d-145">**/del**</span><span class="sxs-lookup"><span data-stu-id="e983d-145">**/del**</span></span>|<span data-ttu-id="e983d-146">Удаляет сертификаты, CTL и CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-146">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="e983d-147">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="e983d-147">**/e** *encodingType*</span></span>|<span data-ttu-id="e983d-148">Указывает тип шифрования сертификата.</span><span class="sxs-lookup"><span data-stu-id="e983d-148">Specifies the certificate encoding type.</span></span> <span data-ttu-id="e983d-149">Значение по умолчанию — `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="e983d-149">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="e983d-150">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="e983d-150">**/f** *dwFlags*</span></span>|<span data-ttu-id="e983d-151">Задает открытый флаг хранилища.</span><span class="sxs-lookup"><span data-stu-id="e983d-151">Specifies the store open flag.</span></span> <span data-ttu-id="e983d-152">Это параметр *dwFlags*, передаваемый методу **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="e983d-152">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="e983d-153">По умолчанию используется значение CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="e983d-153">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="e983d-154">Этот параметр обрабатывается, только если задан параметр **/y**.</span><span class="sxs-lookup"><span data-stu-id="e983d-154">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="e983d-155">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="e983d-155">**/h**[**elp**]</span></span>|<span data-ttu-id="e983d-156">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="e983d-156">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="e983d-157">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="e983d-157">**/n** *nam*</span></span>|<span data-ttu-id="e983d-158">Задает общее имя добавляемого, удаляемого или сохраняемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="e983d-158">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="e983d-159">Этот параметр может применяться только для сертификатов, его нельзя задавать для CTL и CRL.</span><span class="sxs-lookup"><span data-stu-id="e983d-159">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="e983d-160">**/put**</span><span class="sxs-lookup"><span data-stu-id="e983d-160">**/put**</span></span>|<span data-ttu-id="e983d-161">Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-161">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="e983d-162">Файл сохраняется в формате X.509.</span><span class="sxs-lookup"><span data-stu-id="e983d-162">The file is saved in X.509 format.</span></span> <span data-ttu-id="e983d-163">Чтобы сохранить файл в формате PKCS #7, можно использовать параметр **/7** с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-163">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="e983d-164">За параметром **/put** должен следовать параметр **/c**, **/CTL** или **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="e983d-164">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="e983d-165">Параметр **/all** нельзя использовать вместе с параметром **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-165">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="e983d-166">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="e983d-166">**/r** *location*</span></span>|<span data-ttu-id="e983d-167">Указывает расположение системного хранилища в реестре.</span><span class="sxs-lookup"><span data-stu-id="e983d-167">Identifies the registry location of the system store.</span></span> <span data-ttu-id="e983d-168">Этот параметр обрабатывается, только если задан параметр **/s**.</span><span class="sxs-lookup"><span data-stu-id="e983d-168">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="e983d-169">Параметр *location* должен иметь одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="e983d-169">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="e983d-170">-   `currentUser` означает, что хранилище сертификатов находится в разделе HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="e983d-170">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="e983d-171">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e983d-171">This is the default.</span></span><br /><span data-ttu-id="e983d-172">-   `localMachine` означает, что хранилище сертификатов находится в разделе HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="e983d-172">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="e983d-173">**/s**</span><span class="sxs-lookup"><span data-stu-id="e983d-173">**/s**</span></span>|<span data-ttu-id="e983d-174">Означает, что хранилище сертификатов является системным.</span><span class="sxs-lookup"><span data-stu-id="e983d-174">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="e983d-175">Если этот параметр не задан, хранилищем считается **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="e983d-175">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="e983d-176">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="e983d-176">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="e983d-177">Задает хэш SHA1 добавляемого, удаляемого или сохраняемого сертификата, CTL или CRL.</span><span class="sxs-lookup"><span data-stu-id="e983d-177">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="e983d-178">**/v**</span><span class="sxs-lookup"><span data-stu-id="e983d-178">**/v**</span></span>|<span data-ttu-id="e983d-179">Включает отображение подробных сведений о сертификатах, CTL и CRL.</span><span class="sxs-lookup"><span data-stu-id="e983d-179">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="e983d-180">Этот параметр невозможно использовать с параметрами **/add**, **/del** или **/put**.</span><span class="sxs-lookup"><span data-stu-id="e983d-180">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="e983d-181">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="e983d-181">**/y** *provider*</span></span>|<span data-ttu-id="e983d-182">Задает имя поставщика хранилища.</span><span class="sxs-lookup"><span data-stu-id="e983d-182">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="e983d-183">**/7**</span><span class="sxs-lookup"><span data-stu-id="e983d-183">**/7**</span></span>|<span data-ttu-id="e983d-184">Сохраняет конечное хранилище как объект PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="e983d-184">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="e983d-185">**/?**</span><span class="sxs-lookup"><span data-stu-id="e983d-185">**/?**</span></span>|<span data-ttu-id="e983d-186">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="e983d-186">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e983d-187">Примечания</span><span class="sxs-lookup"><span data-stu-id="e983d-187">Remarks</span></span>  

 <span data-ttu-id="e983d-188">Основные функции программы Certmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="e983d-188">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="e983d-189">Отображение сведений о сертификатах, CTL и CRL на консоли.</span><span class="sxs-lookup"><span data-stu-id="e983d-189">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="e983d-190">Добавляет сертификаты, CTL и CRL в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-190">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="e983d-191">Удаляет сертификаты, CTL и CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-191">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="e983d-192">Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-192">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="e983d-193">Программа Certmgr.exe работает с двумя типами хранилищ сертификатов: системным и **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="e983d-193">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="e983d-194">Указывать тип хранилища необязательно, поскольку программа Cedrtmgr.exe может автоматически определить тип хранилища и выполнить соответствующие действия.</span><span class="sxs-lookup"><span data-stu-id="e983d-194">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="e983d-195">При запуске программы Certmgr.exe без параметров выполняется оснастка "certmgr.msc" с графическим интерфейсом пользователя, облегчающим управление сертификатами, что также можно сделать из командной строки.</span><span class="sxs-lookup"><span data-stu-id="e983d-195">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="e983d-196">В графическом интерфейсе пользователя имеется мастер импорта, копирующий сертификаты, CTL и CRL с диска в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-196">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="e983d-197">Чтобы найти имена хранилищ X509Certificate для параметров `sourceStorename` и `destinationStorename`, можно скомпилировать и выполнить следующий код.</span><span class="sxs-lookup"><span data-stu-id="e983d-197">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="e983d-198">Дополнительные сведения см. в разделе [Работа с сертификатами](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e983d-198">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e983d-199">Примеры</span><span class="sxs-lookup"><span data-stu-id="e983d-199">Examples</span></span>  

 <span data-ttu-id="e983d-200">Следующая команда выводит подробные сведения о содержимом системного хранилища `my`, используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e983d-200">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="e983d-201">Следующая команда добавляет все сертификаты из файла `myFile.ext` в новый файл `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="e983d-201">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="e983d-202">Следующая команда добавляет сертификат в файле `testcert.cer` в хранилище системы `my`.</span><span class="sxs-lookup"><span data-stu-id="e983d-202">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="e983d-203">Следующая команда добавляет сертификат в файле `TrustedCert.cer` в хранилище корневых сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e983d-203">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="e983d-204">Следующая команда сохраняет сертификат с общим именем `myCert` в системном хранилище `my` в файл `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="e983d-204">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="e983d-205">Следующая команда удаляет все CTL из системного хранилища `my` и сохраняет полученное хранилище в файл `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="e983d-205">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="e983d-206">Следующая команда сохраняет сертификат в системном хранилище `my` в файл `newFile`.</span><span class="sxs-lookup"><span data-stu-id="e983d-206">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="e983d-207">Программа запросит у пользователя номер сертификата из хранилища `my`, который следует поместить в файл `newFile`.</span><span class="sxs-lookup"><span data-stu-id="e983d-207">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="e983d-208">См. также</span><span class="sxs-lookup"><span data-stu-id="e983d-208">See also</span></span>

- [<span data-ttu-id="e983d-209">Инструменты</span><span class="sxs-lookup"><span data-stu-id="e983d-209">Tools</span></span>](index.md)
- [<span data-ttu-id="e983d-210">Makecert.exe (средство создания сертификатов)</span><span class="sxs-lookup"><span data-stu-id="e983d-210">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="e983d-211">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="e983d-211">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
