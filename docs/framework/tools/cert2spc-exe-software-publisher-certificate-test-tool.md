---
title: Cert2spc.exe (средство проверки сертификата издателя программного обеспечения)
description: Используйте Cert2spc.exe, средство проверки сертификата издателя программного обеспечения. Это средство создает сертификат издателя программного обеспечения (SPC) из одного или более сертификатов X.509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 96b4c05f6c9af6fc78aa55b248a88de84e2d4ac8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258288"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="cfaff-104">Cert2spc.exe (средство проверки сертификата издателя программного обеспечения)</span><span class="sxs-lookup"><span data-stu-id="cfaff-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>

<span data-ttu-id="cfaff-105">Программа для проверки сертификата издателя программного обеспечения служит для создания сертификата издателя программного обеспечения (SPC) из одного или нескольких сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="cfaff-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="cfaff-106">Программа Cert2spc.exe используется только для тестирования.</span><span class="sxs-lookup"><span data-stu-id="cfaff-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="cfaff-107">Действительный сертификат SPC можно получить в центрах сертификации, таких как VeriSign и Thawte.</span><span class="sxs-lookup"><span data-stu-id="cfaff-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="cfaff-108">Дополнительные сведения о создании сертификатов X.509 см. в разделе [Makecert.exe (средство создания сертификатов)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="cfaff-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="cfaff-109">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfaff-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="cfaff-110">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="cfaff-110">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="cfaff-111">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="cfaff-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfaff-112">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cfaff-112">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfaff-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="cfaff-113">Parameters</span></span>  
  
|<span data-ttu-id="cfaff-114">Аргумент</span><span class="sxs-lookup"><span data-stu-id="cfaff-114">Argument</span></span>|<span data-ttu-id="cfaff-115">Описание</span><span class="sxs-lookup"><span data-stu-id="cfaff-115">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="cfaff-116">Имя сертификата X.509, включаемого в SPC-файл.</span><span class="sxs-lookup"><span data-stu-id="cfaff-116">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="cfaff-117">Можно указать несколько имен, разделенных пробелами.</span><span class="sxs-lookup"><span data-stu-id="cfaff-117">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="cfaff-118">Имя списка отзыва сертификатов для включения в SPC-файл.</span><span class="sxs-lookup"><span data-stu-id="cfaff-118">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="cfaff-119">Можно указать несколько имен, разделенных пробелами.</span><span class="sxs-lookup"><span data-stu-id="cfaff-119">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="cfaff-120">Имя объекта PKCS #7, который будет содержать сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="cfaff-120">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="cfaff-121">Параметр</span><span class="sxs-lookup"><span data-stu-id="cfaff-121">Option</span></span>|<span data-ttu-id="cfaff-122">Описание</span><span class="sxs-lookup"><span data-stu-id="cfaff-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cfaff-123">**/?**</span><span class="sxs-lookup"><span data-stu-id="cfaff-123">**/?**</span></span>|<span data-ttu-id="cfaff-124">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="cfaff-124">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="cfaff-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="cfaff-125">Examples</span></span>  

 <span data-ttu-id="cfaff-126">Следующая команда создает SPC-файл из файла `myCertificate.cer` и помещает его в файл `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="cfaff-126">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="cfaff-127">Следующая команда создает SPC-файл из файлов `oneCertificate.cer` и `twoCertificate.cer` и помещает его в файл `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="cfaff-127">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfaff-128">См. также</span><span class="sxs-lookup"><span data-stu-id="cfaff-128">See also</span></span>

- [<span data-ttu-id="cfaff-129">Инструменты</span><span class="sxs-lookup"><span data-stu-id="cfaff-129">Tools</span></span>](index.md)
- [<span data-ttu-id="cfaff-130">Makecert.exe (средство создания сертификатов)</span><span class="sxs-lookup"><span data-stu-id="cfaff-130">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="cfaff-131">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="cfaff-131">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
