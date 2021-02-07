---
description: 'Дополнительные сведения о: ServiceMetadataBehavior'
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1b1438013ec667b10b300d898687abf6f33f96fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715487"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="03e5d-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="03e5d-103">ServiceMetadataBehavior</span></span>

<span data-ttu-id="03e5d-104">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="03e5d-104">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e5d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03e5d-105">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="03e5d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="03e5d-106">Methods</span></span>  

 <span data-ttu-id="03e5d-107">Класс ServiceMetadataBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="03e5d-107">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="03e5d-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="03e5d-108">Properties</span></span>  

 <span data-ttu-id="03e5d-109">Класс ServiceMetadataBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="03e5d-109">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="03e5d-110">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="03e5d-110">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="03e5d-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="03e5d-111">Data type: string</span></span>  
  
 <span data-ttu-id="03e5d-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="03e5d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03e5d-113">Задает расположение, в которое служба перенаправляет запросы метаданных.</span><span class="sxs-lookup"><span data-stu-id="03e5d-113">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="03e5d-114">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="03e5d-114">HttpGetEnabled</span></span>  

 <span data-ttu-id="03e5d-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="03e5d-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="03e5d-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="03e5d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03e5d-117">Определяет, публикует ли служба свой код WSDL по адресу, определяемому атрибутом `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="03e5d-117">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="03e5d-118">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="03e5d-118">HttpGetUrl</span></span>  

 <span data-ttu-id="03e5d-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="03e5d-119">Data type: string</span></span>  
  
 <span data-ttu-id="03e5d-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="03e5d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03e5d-121">Задает расположение для публикации языка WSDL службы и его получения с помощью HTTP.</span><span class="sxs-lookup"><span data-stu-id="03e5d-121">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="03e5d-122">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="03e5d-122">HttpsGetEnabled</span></span>  

 <span data-ttu-id="03e5d-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="03e5d-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="03e5d-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="03e5d-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03e5d-125">Определяет, публикует ли служба свой язык WSDL через HTTPS по адресу, указанному в атрибуте `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="03e5d-125">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="03e5d-126">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="03e5d-126">HttpsGetUrl</span></span>  

 <span data-ttu-id="03e5d-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="03e5d-127">Data type: string</span></span>  
  
 <span data-ttu-id="03e5d-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="03e5d-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03e5d-129">Задает расположение для публикации языка WSDL службы и его получения с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03e5d-129">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e5d-130">Требования</span><span class="sxs-lookup"><span data-stu-id="03e5d-130">Requirements</span></span>  
  
|<span data-ttu-id="03e5d-131">MOF</span><span class="sxs-lookup"><span data-stu-id="03e5d-131">MOF</span></span>|<span data-ttu-id="03e5d-132">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="03e5d-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="03e5d-133">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="03e5d-133">Namespace</span></span>|<span data-ttu-id="03e5d-134">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="03e5d-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03e5d-135">См. также</span><span class="sxs-lookup"><span data-stu-id="03e5d-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
