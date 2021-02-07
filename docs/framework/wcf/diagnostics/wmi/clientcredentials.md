---
description: 'Дополнительные сведения: ClientCredentials'
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 7b0b5a05e5b61de717567de664079f2ed1e20f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757667"
---
# <a name="clientcredentials"></a><span data-ttu-id="1c79a-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="1c79a-103">ClientCredentials</span></span>

<span data-ttu-id="1c79a-104">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="1c79a-104">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c79a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c79a-105">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c79a-106">Методы</span><span class="sxs-lookup"><span data-stu-id="1c79a-106">Methods</span></span>  

 <span data-ttu-id="1c79a-107">Класс ClientCredentials не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="1c79a-107">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c79a-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="1c79a-108">Properties</span></span>  

 <span data-ttu-id="1c79a-109">Класс ClientCredentials имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="1c79a-109">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="1c79a-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1c79a-110">ClientCertificate</span></span>  

 <span data-ttu-id="1c79a-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-111">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-113">Сертификат X.509, используемый клиентом для проверки подлинности службы.</span><span class="sxs-lookup"><span data-stu-id="1c79a-113">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="1c79a-114">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="1c79a-114">HttpDigest</span></span>  

 <span data-ttu-id="1c79a-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-115">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-117">Текущие учетные данные хэш-кода HTTP.</span><span class="sxs-lookup"><span data-stu-id="1c79a-117">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="1c79a-118">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="1c79a-118">IssuedToken</span></span>  

 <span data-ttu-id="1c79a-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-119">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-121">Адрес конечной точки и привязка, используемые для связи с локальной службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="1c79a-121">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="1c79a-122">Одноранговый узел</span><span class="sxs-lookup"><span data-stu-id="1c79a-122">Peer</span></span>  

 <span data-ttu-id="1c79a-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-123">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-125">Учетные данные, используемые одноранговым узлом для подтверждения своей подлинности при подключении к другим узлам в сетке.</span><span class="sxs-lookup"><span data-stu-id="1c79a-125">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="1c79a-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="1c79a-126">ServiceCertificate</span></span>  

 <span data-ttu-id="1c79a-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-127">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-129">Сертификат X.509 службы.</span><span class="sxs-lookup"><span data-stu-id="1c79a-129">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="1c79a-130">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="1c79a-130">SupportInteractive</span></span>  

 <span data-ttu-id="1c79a-131">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="1c79a-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c79a-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-133">Логическое значение, определяющее, поддерживают ли учетные данные интерактивное согласование.</span><span class="sxs-lookup"><span data-stu-id="1c79a-133">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="1c79a-134">UserName</span><span class="sxs-lookup"><span data-stu-id="1c79a-134">UserName</span></span>  

 <span data-ttu-id="1c79a-135">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-135">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-137">Имя пользователя и пароль, используемые клиентом для подтверждения своей подлинности при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="1c79a-137">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="1c79a-138">Windows</span><span class="sxs-lookup"><span data-stu-id="1c79a-138">Windows</span></span>  

 <span data-ttu-id="1c79a-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="1c79a-139">Data type: string</span></span>  
  
 <span data-ttu-id="1c79a-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1c79a-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c79a-141">Учетные данные Windows, используемые клиентом для подтверждения своей подлинности при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="1c79a-141">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c79a-142">Требования</span><span class="sxs-lookup"><span data-stu-id="1c79a-142">Requirements</span></span>  
  
|<span data-ttu-id="1c79a-143">MOF</span><span class="sxs-lookup"><span data-stu-id="1c79a-143">MOF</span></span>|<span data-ttu-id="1c79a-144">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c79a-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c79a-145">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="1c79a-145">Namespace</span></span>|<span data-ttu-id="1c79a-146">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="1c79a-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c79a-147">См. также</span><span class="sxs-lookup"><span data-stu-id="1c79a-147">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
