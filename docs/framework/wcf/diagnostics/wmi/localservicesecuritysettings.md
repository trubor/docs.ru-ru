---
description: 'Дополнительные сведения о: Локалсервицесекуритисеттингс'
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: f7220e8253c6ab218414c1be7ed90e5d593b4692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743945"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="fb2d8-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fb2d8-103">LocalServiceSecuritySettings</span></span>

<span data-ttu-id="fb2d8-104">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fb2d8-104">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2d8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb2d8-105">Syntax</span></span>  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fb2d8-106">Методы</span><span class="sxs-lookup"><span data-stu-id="fb2d8-106">Methods</span></span>  

 <span data-ttu-id="fb2d8-107">Класс LocalServiceSecuritySettings не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-107">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fb2d8-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="fb2d8-108">Properties</span></span>  

 <span data-ttu-id="fb2d8-109">Класс LocalServiceSecuritySettings имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-109">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="fb2d8-110">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="fb2d8-110">DetectReplays</span></span>  

 <span data-ttu-id="fb2d8-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="fb2d8-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="fb2d8-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-113">Логическое значение, показывающее, будут ли атаки с повторением обнаружены и ликвидированы на канале автоматически.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-113">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="fb2d8-114">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="fb2d8-114">InactivityTimeout</span></span>  

 <span data-ttu-id="fb2d8-115">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-117">Максимальное количество ожидающих безопасных сеансов, поддерживаемое службой.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-117">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="fb2d8-118">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-118">IssuedCookieLifetime</span></span>  

 <span data-ttu-id="fb2d8-119">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-121">Значение типа TimeSpan, которое задает время существования для всех новых файлов безопасности cookie.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-121">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="fb2d8-122">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="fb2d8-122">MaxCachedCookies</span></span>  

 <span data-ttu-id="fb2d8-123">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb2d8-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb2d8-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-125">Максимальное количество файлов cookie, которые могут быть кэшированы.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-125">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="fb2d8-126">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="fb2d8-126">MaxClockSkew</span></span>  

 <span data-ttu-id="fb2d8-127">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-129">Значение типа TimeSpan, указывающее максимальный разброс времени между системными часами взаимодействующих сторон.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-129">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="fb2d8-130">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="fb2d8-130">MaxPendingSessions</span></span>  

 <span data-ttu-id="fb2d8-131">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb2d8-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb2d8-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-133">Максимальное количество ожидающих подключений к службе.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-133">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="fb2d8-134">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="fb2d8-134">MaxStatefulNegotiations</span></span>  

 <span data-ttu-id="fb2d8-135">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb2d8-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb2d8-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-137">Количество одновременно выполняемых согласований режима безопасности.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-137">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="fb2d8-138">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="fb2d8-138">NegotiationTimeout</span></span>  

 <span data-ttu-id="fb2d8-139">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-141">Значение типа TimeSpan, указывающее максимальную длительность этапа согласования режима безопасности между сервером и клиентом.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-141">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="fb2d8-142">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="fb2d8-142">ReconnectTransportOnFailure</span></span>  

 <span data-ttu-id="fb2d8-143">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="fb2d8-143">Data type: boolean</span></span>  
  
 <span data-ttu-id="fb2d8-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-145">Логическое значение, указывающее, будут ли подключения, использующие режим обмена сообщениями WS-Reliable, пытаться восстановиться после транспортных сбоев.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-145">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="fb2d8-146">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="fb2d8-146">ReplayCacheSize</span></span>  

 <span data-ttu-id="fb2d8-147">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="fb2d8-147">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb2d8-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-149">Количество кэшированных параметров nonce, используемых для определения ответов.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-149">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="fb2d8-150">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="fb2d8-150">ReplayWindow</span></span>  

 <span data-ttu-id="fb2d8-151">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-151">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-153">Значение типа TimeSpan, которое указывает срок действия параметров nonce отдельного сообщения.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-153">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="fb2d8-154">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="fb2d8-154">SessionKeyRenewalInterval</span></span>  

 <span data-ttu-id="fb2d8-155">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-155">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-157">Значение типа TimeSpan, которое задает интервал времени, по истечении которого инициатор обновляет ключ сеанса безопасности.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-157">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="fb2d8-158">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="fb2d8-158">SessionKeyRolloverInterval</span></span>  

 <span data-ttu-id="fb2d8-159">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-160">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-161">Значение типа TimeSpan, которое задает интервал времени, указывающий период, в течение которого предыдущий сеансовый ключ остается действительным для входящих сообщений, пока выполняется обновление ключа.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-161">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="fb2d8-162">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="fb2d8-162">TimestampValidityDuration</span></span>  

 <span data-ttu-id="fb2d8-163">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="fb2d8-163">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2d8-164">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="fb2d8-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2d8-165">Значение типа TimeSpan, которое определяет интервал времени, указывающий срок действия отметки времени.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-165">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb2d8-166">Требования</span><span class="sxs-lookup"><span data-stu-id="fb2d8-166">Requirements</span></span>  
  
|<span data-ttu-id="fb2d8-167">MOF</span><span class="sxs-lookup"><span data-stu-id="fb2d8-167">MOF</span></span>|<span data-ttu-id="fb2d8-168">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-168">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fb2d8-169">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="fb2d8-169">Namespace</span></span>|<span data-ttu-id="fb2d8-170">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-170">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb2d8-171">См. также</span><span class="sxs-lookup"><span data-stu-id="fb2d8-171">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
