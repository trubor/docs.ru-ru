---
description: 'Дополнительные сведения о: ServiceDebugBehavior'
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 3b384c209524267c72a12d96bc845b694144ba19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715539"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="d2aea-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d2aea-103">ServiceDebugBehavior</span></span>

<span data-ttu-id="d2aea-104">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d2aea-104">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2aea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2aea-105">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d2aea-106">Методы</span><span class="sxs-lookup"><span data-stu-id="d2aea-106">Methods</span></span>  

 <span data-ttu-id="d2aea-107">Класс ServiceDebugBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="d2aea-107">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d2aea-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="d2aea-108">Properties</span></span>  

 <span data-ttu-id="d2aea-109">Класс ServiceDebugBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="d2aea-109">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="d2aea-110">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d2aea-110">HttpHelpPageEnabled</span></span>  

 <span data-ttu-id="d2aea-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="d2aea-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="d2aea-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d2aea-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2aea-113">Определяет, публикует ли служба свой код WSDL по адресу, определяемому атрибутом `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="d2aea-113">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="d2aea-114">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d2aea-114">HttpHelpPageUrl</span></span>  

 <span data-ttu-id="d2aea-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d2aea-115">Data type: string</span></span>  
  
 <span data-ttu-id="d2aea-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d2aea-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2aea-117">Задает расположение для публикации языка WSDL службы и его получения с помощью HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2aea-117">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="d2aea-118">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d2aea-118">HttpsHelpPageEnabled</span></span>  

 <span data-ttu-id="d2aea-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="d2aea-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="d2aea-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d2aea-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2aea-121">Определяет, публикует ли служба свой язык WSDL через HTTPS по адресу, указанному в атрибуте `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="d2aea-121">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="d2aea-122">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d2aea-122">HttpsHelpPageUrl</span></span>  

 <span data-ttu-id="d2aea-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d2aea-123">Data type: string</span></span>  
  
 <span data-ttu-id="d2aea-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d2aea-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2aea-125">Задает расположение для публикации языка WSDL службы и его получения с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d2aea-125">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d2aea-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d2aea-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="d2aea-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="d2aea-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="d2aea-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d2aea-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2aea-129">Указывает, включать ли информацию об управляемых исключениях в сведения об ошибках SOAP, возвращаемые клиентам для отладки.</span><span class="sxs-lookup"><span data-stu-id="d2aea-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2aea-130">Требования</span><span class="sxs-lookup"><span data-stu-id="d2aea-130">Requirements</span></span>  
  
|<span data-ttu-id="d2aea-131">MOF</span><span class="sxs-lookup"><span data-stu-id="d2aea-131">MOF</span></span>|<span data-ttu-id="d2aea-132">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d2aea-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d2aea-133">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="d2aea-133">Namespace</span></span>|<span data-ttu-id="d2aea-134">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d2aea-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2aea-135">См. также</span><span class="sxs-lookup"><span data-stu-id="d2aea-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
