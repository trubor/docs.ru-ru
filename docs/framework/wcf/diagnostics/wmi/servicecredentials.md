---
description: 'Дополнительные сведения о: ServiceCredentials'
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bfd025a8f671a3c5aea537059cde0e751cfa9bb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715552"
---
# <a name="servicecredentials"></a><span data-ttu-id="c9227-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="c9227-103">ServiceCredentials</span></span>

<span data-ttu-id="c9227-104">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="c9227-104">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9227-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9227-105">Syntax</span></span>  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c9227-106">Методы</span><span class="sxs-lookup"><span data-stu-id="c9227-106">Methods</span></span>  

 <span data-ttu-id="c9227-107">Класс ServiceCredentials не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="c9227-107">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9227-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="c9227-108">Properties</span></span>  

 <span data-ttu-id="c9227-109">Класс ServiceCredentials имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="c9227-109">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="c9227-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c9227-110">ClientCertificate</span></span>  

 <span data-ttu-id="c9227-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-111">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-113">Параметры проверки подлинности сертификата клиента и подготовки для этой службы.</span><span class="sxs-lookup"><span data-stu-id="c9227-113">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="c9227-114">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9227-114">IssuedTokenAuthentication</span></span>  

 <span data-ttu-id="c9227-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-115">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-117">Параметры проверки подлинности текущего выданного маркера для этой службы.</span><span class="sxs-lookup"><span data-stu-id="c9227-117">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="c9227-118">Одноранговый узел</span><span class="sxs-lookup"><span data-stu-id="c9227-118">Peer</span></span>  

 <span data-ttu-id="c9227-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-119">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-121">Текущие параметры проверки подлинности учетных данных и подготовки для использования конечными точками однорангового транспорта.</span><span class="sxs-lookup"><span data-stu-id="c9227-121">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="c9227-122">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9227-122">SecureConversationAuthentication</span></span>  

 <span data-ttu-id="c9227-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-123">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-125">Задает текущие параметры безопасного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="c9227-125">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="c9227-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="c9227-126">ServiceCertificate</span></span>  

 <span data-ttu-id="c9227-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-127">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-129">Сертификат, связанный с этой службой.</span><span class="sxs-lookup"><span data-stu-id="c9227-129">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="c9227-130">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9227-130">UserNameAuthentication</span></span>  

 <span data-ttu-id="c9227-131">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-131">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-133">Параметры проверки имени пользователя и пароля для данной службы.</span><span class="sxs-lookup"><span data-stu-id="c9227-133">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="c9227-134">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9227-134">WindowsAuthentication</span></span>  

 <span data-ttu-id="c9227-135">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c9227-135">Data type: string</span></span>  
  
 <span data-ttu-id="c9227-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c9227-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9227-137">Параметры проверки подлинности Windows для этой службы.</span><span class="sxs-lookup"><span data-stu-id="c9227-137">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9227-138">Требования</span><span class="sxs-lookup"><span data-stu-id="c9227-138">Requirements</span></span>  
  
|<span data-ttu-id="c9227-139">MOF</span><span class="sxs-lookup"><span data-stu-id="c9227-139">MOF</span></span>|<span data-ttu-id="c9227-140">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c9227-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c9227-141">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="c9227-141">Namespace</span></span>|<span data-ttu-id="c9227-142">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="c9227-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9227-143">См. также</span><span class="sxs-lookup"><span data-stu-id="c9227-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
