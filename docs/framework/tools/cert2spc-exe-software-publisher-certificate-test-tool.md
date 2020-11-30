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
ms.openlocfilehash: 0bcc785a51f2ca46195970130178d0cfa705ee6e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247327"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="70a89-104">Cert2spc.exe (средство проверки сертификата издателя программного обеспечения)</span><span class="sxs-lookup"><span data-stu-id="70a89-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>

<span data-ttu-id="70a89-105">Программа для проверки сертификата издателя программного обеспечения служит для создания сертификата издателя программного обеспечения (SPC) из одного или нескольких сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="70a89-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="70a89-106">Программа Cert2spc.exe используется только для тестирования.</span><span class="sxs-lookup"><span data-stu-id="70a89-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="70a89-107">Действительный сертификат SPC можно получить в центрах сертификации, таких как VeriSign и Thawte.</span><span class="sxs-lookup"><span data-stu-id="70a89-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="70a89-108">Дополнительные сведения о создании сертификатов X.509 см. в разделе [Makecert.exe (средство создания сертификатов)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="70a89-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="70a89-109">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70a89-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="70a89-110">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="70a89-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="70a89-111">Дополнительные сведения см. в разделе [Командные строки](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="70a89-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="70a89-112">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="70a89-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a89-113">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="70a89-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="70a89-114">Параметры</span><span class="sxs-lookup"><span data-stu-id="70a89-114">Parameters</span></span>  
  
|<span data-ttu-id="70a89-115">Аргумент</span><span class="sxs-lookup"><span data-stu-id="70a89-115">Argument</span></span>|<span data-ttu-id="70a89-116">Описание</span><span class="sxs-lookup"><span data-stu-id="70a89-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="70a89-117">Имя сертификата X.509, включаемого в SPC-файл.</span><span class="sxs-lookup"><span data-stu-id="70a89-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="70a89-118">Можно указать несколько имен, разделенных пробелами.</span><span class="sxs-lookup"><span data-stu-id="70a89-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="70a89-119">Имя списка отзыва сертификатов для включения в SPC-файл.</span><span class="sxs-lookup"><span data-stu-id="70a89-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="70a89-120">Можно указать несколько имен, разделенных пробелами.</span><span class="sxs-lookup"><span data-stu-id="70a89-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="70a89-121">Имя объекта PKCS #7, который будет содержать сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="70a89-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="70a89-122">Параметр</span><span class="sxs-lookup"><span data-stu-id="70a89-122">Option</span></span>|<span data-ttu-id="70a89-123">Описание</span><span class="sxs-lookup"><span data-stu-id="70a89-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="70a89-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="70a89-124">**/?**</span></span>|<span data-ttu-id="70a89-125">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="70a89-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="70a89-126">Примеры</span><span class="sxs-lookup"><span data-stu-id="70a89-126">Examples</span></span>  

 <span data-ttu-id="70a89-127">Следующая команда создает SPC-файл из файла `myCertificate.cer` и помещает его в файл `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="70a89-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="70a89-128">Следующая команда создает SPC-файл из файлов `oneCertificate.cer` и `twoCertificate.cer` и помещает его в файл `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="70a89-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="70a89-129">См. также</span><span class="sxs-lookup"><span data-stu-id="70a89-129">See also</span></span>

- [<span data-ttu-id="70a89-130">Инструменты</span><span class="sxs-lookup"><span data-stu-id="70a89-130">Tools</span></span>](index.md)
- [<span data-ttu-id="70a89-131">Makecert.exe (средство создания сертификатов)</span><span class="sxs-lookup"><span data-stu-id="70a89-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="70a89-132">Командные строки</span><span class="sxs-lookup"><span data-stu-id="70a89-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
