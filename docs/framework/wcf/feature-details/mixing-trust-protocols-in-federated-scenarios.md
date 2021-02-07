---
description: Дополнительные сведения о смешении протоколов доверия в федеративных сценариях
title: Использование нескольких протоколов доверия в сценариях федерации
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: f882b3728ed791f611a9f71f32840e68d8e17a1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733727"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="9f4d4-103">Использование нескольких протоколов доверия в сценариях федерации</span><span class="sxs-lookup"><span data-stu-id="9f4d4-103">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="9f4d4-104">Возможны сценарии, в которых федеративные клиенты взаимодействуют со службой и службой маркеров безопасности, версии доверия которых не совпадают.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-104">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="9f4d4-105">Код WSDL службы может содержать утверждение `RequestSecurityTokenTemplate` с элементами WS-Trust, версии которых не совпадают с версией службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-105">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="9f4d4-106">В таких случаях клиент Windows Communication Foundation (WCF) преобразует элементы WS-Trust, полученные из, в, `RequestSecurityTokenTemplate` чтобы соответствовать версии доверия STS.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-106">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="9f4d4-107">WCF обрабатывает несоответствующие версии доверия только для стандартных привязок.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-107">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="9f4d4-108">Все стандартные параметры алгоритма, распознаваемые WCF, являются частью стандартной привязки.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-108">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="9f4d4-109">В этом разделе описывается поведение WCF с различными параметрами доверия между службой и STS.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-109">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="9f4d4-110">Проверяющая сторона и служба маркеров безопасности используют версию февраля 2005 г.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-110">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="9f4d4-111">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="9f4d4-111">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="9f4d4-112">Файл конфигурации клиента содержит список параметров.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-112">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="9f4d4-113">WCF не может различить параметры клиента и службы; Он добавляет все параметры и отправляет их в `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="9f4d4-113">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="9f4d4-114">Проверяющая сторона и служба маркеров безопасности используют версию Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="9f4d4-114">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="9f4d4-115">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="9f4d4-115">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="9f4d4-116">Файл конфигурации клиента содержит элемент `secondaryParameters`, являющийся оболочкой для параметров, заданных проверяющей стороной.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-116">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="9f4d4-117">WCF удаляет `EncryptionAlgorithm` `CanonicalizationAlgorithm` `KeyWrapAlgorithm` элементы и из элемента верхнего уровня в RST, если они существуют внутри `SecondaryParameters` элемента.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-117">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="9f4d4-118">WCF добавляет `SecondaryParameters` элемент в исходящий RST без изменений.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-118">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="9f4d4-119">Проверяющая сторона использует версию февраля 2005 г., а служба маркеров безопасности - версию Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="9f4d4-119">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="9f4d4-120">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="9f4d4-120">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="9f4d4-121">Файл конфигурации клиента содержит список параметров.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-121">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="9f4d4-122">В файле конфигурации клиента WCF не может различить параметры службы и клиента.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-122">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="9f4d4-123">Поэтому WCF преобразует все параметры в пространство имен доверия версии 1,3.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-123">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="9f4d4-124">WCF обрабатывает `KeyType` элементы, `KeySize` и `TokenType` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9f4d4-124">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="9f4d4-125">Загружается код WSDL, создается привязка и присваиваются значения `KeyType`, `KeySize` и `TokenType` на основании параметров проверяющей стороны.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-125">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="9f4d4-126">Создается файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-126">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="9f4d4-127">Теперь клиент может изменять любые параметры в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-127">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="9f4d4-128">Во время выполнения WCF копирует все параметры, указанные в `AdditionalTokenParameters` разделе файла конфигурации клиента, за исключением `KeyType` `KeySize` и `TokenType` , поскольку эти параметры задаются во время создания файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-128">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="9f4d4-129">Проверяющая сторона использует версию Trust 1.3, а служба маркеров безопасности - версию февраля 2005 г.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-129">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="9f4d4-130">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="9f4d4-130">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="9f4d4-131">Файл конфигурации клиента содержит элемент `secondaryParamters`, являющийся оболочкой для параметров, заданных проверяющей стороной.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-131">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="9f4d4-132">WCF копирует все параметры, указанные в `SecondaryParameters` разделе, в элемент RST верхнего уровня, но не преобразует их в пространство имен 2005 WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-132">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
