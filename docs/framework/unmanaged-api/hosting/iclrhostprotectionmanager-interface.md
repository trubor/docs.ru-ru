---
description: 'Дополнительные сведения о: интерфейс Иклрхостпротектионманажер'
title: Интерфейс ICLRHostProtectionManager
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689252"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="9f217-103">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="9f217-103">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="9f217-104">Позволяет узлу блокировать выполнение конкретных управляемых классов, методов, свойств и полей в частично доверяемом коде.</span><span class="sxs-lookup"><span data-stu-id="9f217-104">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f217-105">Методы</span><span class="sxs-lookup"><span data-stu-id="9f217-105">Methods</span></span>  
  
|<span data-ttu-id="9f217-106">Метод</span><span class="sxs-lookup"><span data-stu-id="9f217-106">Method</span></span>|<span data-ttu-id="9f217-107">Описание</span><span class="sxs-lookup"><span data-stu-id="9f217-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f217-108">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="9f217-108">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="9f217-109">Гарантирует, что некоторые редкие состояния гонки, которые могут вызвать неустранимые ошибки среды CLR, никогда не будут возникать.</span><span class="sxs-lookup"><span data-stu-id="9f217-109">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="9f217-110">Метод SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="9f217-110">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="9f217-111">Указывает категории управляемых типов и членов, выполнение которых должно быть заблокировано в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="9f217-111">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f217-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9f217-112">Requirements</span></span>  

 <span data-ttu-id="9f217-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f217-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f217-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f217-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f217-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f217-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f217-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f217-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f217-117">См. также</span><span class="sxs-lookup"><span data-stu-id="9f217-117">See also</span></span>

- [<span data-ttu-id="9f217-118">Перечисление EApiCategories</span><span class="sxs-lookup"><span data-stu-id="9f217-118">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="9f217-119">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9f217-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
