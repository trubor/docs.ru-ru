---
description: 'Дополнительные сведения о методе: Икордебугаппдомаиненум:: Next'
title: Метод ICorDebugAppDomainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: ac5397250e661b4ed380b3272744957f86e1a07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791534"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="0e495-103">Метод ICorDebugAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="0e495-103">ICorDebugAppDomainEnum::Next Method</span></span>

<span data-ttu-id="0e495-104">Возвращает указанное число доменов приложений из коллекции, начиная с текущей позиции курсора.</span><span class="sxs-lookup"><span data-stu-id="0e495-104">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e495-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e495-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e495-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e495-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="0e495-107">окне Число извлекаемых доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="0e495-107">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0e495-108">заполняет Массив указателей, каждый из которых указывает на объект ICorDebugAppDomain, представляющий домен приложения.</span><span class="sxs-lookup"><span data-stu-id="0e495-108">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0e495-109">заполняет Указатель на число фактически возвращенных доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="0e495-109">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="0e495-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="0e495-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e495-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0e495-111">Requirements</span></span>  

 <span data-ttu-id="0e495-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e495-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e495-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e495-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e495-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e495-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e495-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e495-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
