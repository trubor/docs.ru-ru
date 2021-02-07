---
description: 'Дополнительные сведения о: ServiceAuthorizationBehavior'
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: dc398621103774a04934aa23ae3d7208f4389717
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715591"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="bdabb-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="bdabb-103">ServiceAuthorizationBehavior</span></span>

<span data-ttu-id="bdabb-104">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="bdabb-104">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdabb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdabb-105">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bdabb-106">Методы</span><span class="sxs-lookup"><span data-stu-id="bdabb-106">Methods</span></span>  

 <span data-ttu-id="bdabb-107">Класс ServiceAuthorizationBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="bdabb-107">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bdabb-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="bdabb-108">Properties</span></span>  

 <span data-ttu-id="bdabb-109">Класс ServiceAuthorizationBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="bdabb-109">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="bdabb-110">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="bdabb-110">ImpersonateCallerForAllOperations</span></span>  

 <span data-ttu-id="bdabb-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="bdabb-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="bdabb-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bdabb-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdabb-113">Значение, которое определяет, будет ли служба пытаться производить олицетворение при помощи учетных данных, содержащихся во входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="bdabb-113">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="bdabb-114">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="bdabb-114">PrincipalPermissionMode</span></span>  

 <span data-ttu-id="bdabb-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="bdabb-115">Data type: string</span></span>  
  
 <span data-ttu-id="bdabb-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bdabb-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdabb-117">Участник, используемый для выполнения операций на сервере.</span><span class="sxs-lookup"><span data-stu-id="bdabb-117">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="bdabb-118">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="bdabb-118">RoleProvider</span></span>  

 <span data-ttu-id="bdabb-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="bdabb-119">Data type: string</span></span>  
  
 <span data-ttu-id="bdabb-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bdabb-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdabb-121">Имя поставщика ролей ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bdabb-121">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="bdabb-122">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="bdabb-122">ServiceAuthorizationManager</span></span>  

 <span data-ttu-id="bdabb-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="bdabb-123">Data type: string</span></span>  
  
 <span data-ttu-id="bdabb-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="bdabb-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdabb-125">Диспетчер авторизации, используемый для пользовательской авторизации.</span><span class="sxs-lookup"><span data-stu-id="bdabb-125">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdabb-126">Требования</span><span class="sxs-lookup"><span data-stu-id="bdabb-126">Requirements</span></span>  
  
|<span data-ttu-id="bdabb-127">MOF</span><span class="sxs-lookup"><span data-stu-id="bdabb-127">MOF</span></span>|<span data-ttu-id="bdabb-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bdabb-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bdabb-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="bdabb-129">Namespace</span></span>|<span data-ttu-id="bdabb-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="bdabb-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdabb-131">См. также</span><span class="sxs-lookup"><span data-stu-id="bdabb-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
