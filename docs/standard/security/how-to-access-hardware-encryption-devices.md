---
description: Дополнительные сведения см. в статье как получить доступ к устройствам шифрования оборудования.
title: Практическое руководство. Доступ к устройствам аппаратного шифрования
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: fcf12314490542848d20bd3a4977d68c386853bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685274"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="95db5-103">Практическое руководство. Доступ к устройствам аппаратного шифрования</span><span class="sxs-lookup"><span data-stu-id="95db5-103">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="95db5-104">Эта статья относится к Windows.</span><span class="sxs-lookup"><span data-stu-id="95db5-104">This article applies to Windows.</span></span>

<span data-ttu-id="95db5-105">Класс <xref:System.Security.Cryptography.CspParameters> можно использовать для доступа к устройствам аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="95db5-105">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="95db5-106">Например, этот класс можно использовать для интеграции приложения со смарт-картой, аппаратным генератором случайных чисел или аппаратной реализацией определенного алгоритма шифрования.</span><span class="sxs-lookup"><span data-stu-id="95db5-106">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="95db5-107">Класс <xref:System.Security.Cryptography.CspParameters> создает поставщик служб шифрования (CSP), который обращается к правильно установленному устройству аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="95db5-107">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="95db5-108">Можно проверить доступность CSP, изучив следующий раздел реестра при помощи редактора реестра (Regedit.exe): HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="95db5-108">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="95db5-109">Подпись данных при помощи карты с ключом</span><span class="sxs-lookup"><span data-stu-id="95db5-109">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="95db5-110">Создайте новый экземпляр класса <xref:System.Security.Cryptography.CspParameters>, передав в конструктор целочисленный тип поставщика и имя поставщика.</span><span class="sxs-lookup"><span data-stu-id="95db5-110">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="95db5-111">Передайте соответствующие флаги в свойство <xref:System.Security.Cryptography.CspParameters.Flags%2A> созданного объекта <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="95db5-111">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="95db5-112">Например, передайте флаг <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.</span><span class="sxs-lookup"><span data-stu-id="95db5-112">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="95db5-113">Создайте новый экземпляр класса <xref:System.Security.Cryptography.AsymmetricAlgorithm>(например, класс <xref:System.Security.Cryptography.RSACryptoServiceProvider>), передав объект <xref:System.Security.Cryptography.CspParameters> в конструктор.</span><span class="sxs-lookup"><span data-stu-id="95db5-113">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="95db5-114">Подпишите данные при помощи одного из методов `Sign` и проверьте данные, используя один из методов `Verify`.</span><span class="sxs-lookup"><span data-stu-id="95db5-114">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="95db5-115">Формирование случайного числа при помощи аппаратного генератора случайных чисел</span><span class="sxs-lookup"><span data-stu-id="95db5-115">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="95db5-116">Создайте новый экземпляр класса <xref:System.Security.Cryptography.CspParameters>, передав в конструктор целочисленный тип поставщика и имя поставщика.</span><span class="sxs-lookup"><span data-stu-id="95db5-116">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="95db5-117">Создайте новый экземпляр <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, передав объект <xref:System.Security.Cryptography.CspParameters> в конструктор.</span><span class="sxs-lookup"><span data-stu-id="95db5-117">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="95db5-118">Создайте случайное значение при помощи метода <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> или <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.</span><span class="sxs-lookup"><span data-stu-id="95db5-118">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95db5-119">Пример</span><span class="sxs-lookup"><span data-stu-id="95db5-119">Example</span></span>

<span data-ttu-id="95db5-120">В примере кода ниже показано, как подписать данные при помощи смарт-карты.</span><span class="sxs-lookup"><span data-stu-id="95db5-120">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="95db5-121">Этот пример кода создает объект <xref:System.Security.Cryptography.CspParameters>, который предоставляет смарт-карты, а затем инициализирует объект <xref:System.Security.Cryptography.RSACryptoServiceProvider> при помощи CSP.</span><span class="sxs-lookup"><span data-stu-id="95db5-121">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="95db5-122">После этого примера подписывает и проверяет некоторые данные.</span><span class="sxs-lookup"><span data-stu-id="95db5-122">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="95db5-123">Из-за проблем с алгоритмом SHA1 рекомендуется использовать SHA256 или более высокий уровень.</span><span class="sxs-lookup"><span data-stu-id="95db5-123">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95db5-124">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="95db5-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="95db5-125">Включите пространства имен <xref:System> и <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="95db5-125">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="95db5-126">На компьютере должно быть установлено устройство чтения смарт-карт и соответствующие драйвера.</span><span class="sxs-lookup"><span data-stu-id="95db5-126">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="95db5-127">Необходимо инициализировать объект <xref:System.Security.Cryptography.CspParameters>, используя информацию, характерную для вашего устройства чтения смарт-карт.</span><span class="sxs-lookup"><span data-stu-id="95db5-127">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="95db5-128">Дополнительные сведения см. в документации по устройству чтения смарт-карт.</span><span class="sxs-lookup"><span data-stu-id="95db5-128">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="95db5-129">См. также</span><span class="sxs-lookup"><span data-stu-id="95db5-129">See also</span></span>

- [<span data-ttu-id="95db5-130">Модель криптографии</span><span class="sxs-lookup"><span data-stu-id="95db5-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="95db5-131">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="95db5-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="95db5-132">Кросс-платформенная криптография</span><span class="sxs-lookup"><span data-stu-id="95db5-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="95db5-133">ASP.NET Core Защита данных</span><span class="sxs-lookup"><span data-stu-id="95db5-133">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
