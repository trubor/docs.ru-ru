---
description: 'Дополнительные сведения о: SecurityBindingElement'
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: bc9a519978a9cccccd80a58abb8d109fa9bc9337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743815"
---
# <a name="securitybindingelement"></a><span data-ttu-id="d05e2-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d05e2-103">SecurityBindingElement</span></span>

<span data-ttu-id="d05e2-104">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d05e2-104">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d05e2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d05e2-105">Syntax</span></span>  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d05e2-106">Методы</span><span class="sxs-lookup"><span data-stu-id="d05e2-106">Methods</span></span>  

 <span data-ttu-id="d05e2-107">Класс SecurityBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="d05e2-107">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d05e2-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="d05e2-108">Properties</span></span>  

 <span data-ttu-id="d05e2-109">Класс SecurityBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="d05e2-109">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="d05e2-110">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d05e2-110">DefaultAlgorithmSuite</span></span>  

 <span data-ttu-id="d05e2-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d05e2-111">Data type: string</span></span>  
  
 <span data-ttu-id="d05e2-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-113">Задает алгоритмы, используемые в сочетании с привязкой.</span><span class="sxs-lookup"><span data-stu-id="d05e2-113">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="d05e2-114">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="d05e2-114">IncludeTimestamp</span></span>  

 <span data-ttu-id="d05e2-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="d05e2-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="d05e2-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-117">Логическое значение, указывающее, будет ли в каждое сообщение вноситься метка времени.</span><span class="sxs-lookup"><span data-stu-id="d05e2-117">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="d05e2-118">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="d05e2-118">KeyEntropyMode</span></span>  

 <span data-ttu-id="d05e2-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d05e2-119">Data type: string</span></span>  
  
 <span data-ttu-id="d05e2-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-121">Источник энтропии, используемый для создания ключей.</span><span class="sxs-lookup"><span data-stu-id="d05e2-121">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="d05e2-122">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d05e2-122">LocalServiceSecuritySettings</span></span>  

 <span data-ttu-id="d05e2-123">Тип данных: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d05e2-123">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="d05e2-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-125">Свойства безопасности для локальной службы, соответствующие данной привязке.</span><span class="sxs-lookup"><span data-stu-id="d05e2-125">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="d05e2-126">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="d05e2-126">MessageSecurityVersion</span></span>  

 <span data-ttu-id="d05e2-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d05e2-127">Data type: string</span></span>  
  
 <span data-ttu-id="d05e2-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-129">Версия, используемая для безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="d05e2-129">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="d05e2-130">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="d05e2-130">SecurityHeaderLayout</span></span>  

 <span data-ttu-id="d05e2-131">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="d05e2-131">Data type: string</span></span>  
  
 <span data-ttu-id="d05e2-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d05e2-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d05e2-133">Порядок элементов в заголовке безопасности для данной привязки.</span><span class="sxs-lookup"><span data-stu-id="d05e2-133">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d05e2-134">Требования</span><span class="sxs-lookup"><span data-stu-id="d05e2-134">Requirements</span></span>  
  
|<span data-ttu-id="d05e2-135">MOF</span><span class="sxs-lookup"><span data-stu-id="d05e2-135">MOF</span></span>|<span data-ttu-id="d05e2-136">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d05e2-136">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d05e2-137">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="d05e2-137">Namespace</span></span>|<span data-ttu-id="d05e2-138">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d05e2-138">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d05e2-139">См. также</span><span class="sxs-lookup"><span data-stu-id="d05e2-139">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
