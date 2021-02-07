---
description: 'Дополнительные сведения о: Сервицесекуритяудитбехавиор'
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 5dfb3a70a80d5dea1ed360dcaf3a0db989bf671b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715474"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="52c87-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="52c87-103">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="52c87-104">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="52c87-104">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c87-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52c87-105">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52c87-106">Методы</span><span class="sxs-lookup"><span data-stu-id="52c87-106">Methods</span></span>  

 <span data-ttu-id="52c87-107">Класс ServiceSecurityAuditBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="52c87-107">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52c87-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="52c87-108">Properties</span></span>  

 <span data-ttu-id="52c87-109">Класс ServiceSecurityAuditBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="52c87-109">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="52c87-110">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="52c87-110">AuditLogLocation</span></span>  

 <span data-ttu-id="52c87-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="52c87-111">Data type: string</span></span>  
  
 <span data-ttu-id="52c87-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="52c87-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c87-113">Местоположение журнала аудита.</span><span class="sxs-lookup"><span data-stu-id="52c87-113">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="52c87-114">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="52c87-114">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="52c87-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="52c87-115">Data type: string</span></span>  
  
 <span data-ttu-id="52c87-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="52c87-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c87-117">Тип уровня проверки подлинности сообщений, используемый для записи в журнал событий аудита.</span><span class="sxs-lookup"><span data-stu-id="52c87-117">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="52c87-118">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="52c87-118">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="52c87-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="52c87-119">Data type: string</span></span>  
  
 <span data-ttu-id="52c87-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="52c87-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c87-121">Типы событий авторизации, записываемых в журнал аудита.</span><span class="sxs-lookup"><span data-stu-id="52c87-121">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="52c87-122">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="52c87-122">SuppressAuditFailure</span></span>  

 <span data-ttu-id="52c87-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="52c87-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="52c87-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="52c87-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c87-125">Логическое значение, задающее поведение для подавления ошибок записи в журнал аудита.</span><span class="sxs-lookup"><span data-stu-id="52c87-125">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c87-126">Требования</span><span class="sxs-lookup"><span data-stu-id="52c87-126">Requirements</span></span>  
  
|<span data-ttu-id="52c87-127">MOF</span><span class="sxs-lookup"><span data-stu-id="52c87-127">MOF</span></span>|<span data-ttu-id="52c87-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="52c87-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52c87-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="52c87-129">Namespace</span></span>|<span data-ttu-id="52c87-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="52c87-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52c87-131">См. также</span><span class="sxs-lookup"><span data-stu-id="52c87-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
