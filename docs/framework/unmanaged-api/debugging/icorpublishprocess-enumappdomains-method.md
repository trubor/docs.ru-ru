---
description: 'Дополнительные сведения о методе: ICorPublishProcess:: Енумаппдомаинс'
title: Метод ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: c7834b23967ab467c1589ee31929bf346b4b3b8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794615"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="e69a2-103">Метод ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="e69a2-103">ICorPublishProcess::EnumAppDomains Method</span></span>

<span data-ttu-id="e69a2-104">Возвращает перечислитель для доменов приложений в процессе, на который ссылается этот [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e69a2-104">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e69a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e69a2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e69a2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e69a2-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="e69a2-107">заполняет Указатель на адрес экземпляра [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) , который позволяет выполнять итерацию по коллекции доменов приложений в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="e69a2-107">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e69a2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e69a2-108">Remarks</span></span>  

 <span data-ttu-id="e69a2-109">Список доменов приложений основан на моментальном снимке доменов приложений, существующих при `EnumAppDomains` вызове метода.</span><span class="sxs-lookup"><span data-stu-id="e69a2-109">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="e69a2-110">Этот метод может быть вызван более одного раза для создания нового списка обновлений.</span><span class="sxs-lookup"><span data-stu-id="e69a2-110">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="e69a2-111">Последующие вызовы этого метода не будут затронуты существующими списками.</span><span class="sxs-lookup"><span data-stu-id="e69a2-111">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="e69a2-112">Если процесс был завершен, `EnumAppDomains` произойдет сбой со ЗНАЧЕНИЕМ HRESULT CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="e69a2-112">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e69a2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e69a2-113">Requirements</span></span>  

 <span data-ttu-id="e69a2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e69a2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e69a2-115">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="e69a2-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e69a2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e69a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e69a2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e69a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69a2-118">См. также</span><span class="sxs-lookup"><span data-stu-id="e69a2-118">See also</span></span>

- [<span data-ttu-id="e69a2-119">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="e69a2-119">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
