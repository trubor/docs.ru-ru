---
description: 'Дополнительные сведения: указатель функции PFN_CLRDataCreateInstance'
title: Указатель функции PFN_CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: fc048f840084eff0270944d3190ccbb153bf22d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800634"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="1d2d1-103">Указатель функции PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="1d2d1-103">PFN_CLRDataCreateInstance Function Pointer</span></span>

<span data-ttu-id="1d2d1-104">Указывает на функцию, которая создает объект интерфейса для указанного целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-104">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2d1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1d2d1-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d2d1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1d2d1-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="1d2d1-107">окне Идентификатор интерфейса, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="1d2d1-108">окне Указатель на реализуемый пользователем объект [ICLRDataTarget](iclrdatatarget-interface.md) , представляющий целевой элемент, для которого создается объект интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="1d2d1-109">заполняет Указатель на адрес возвращенного объекта интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2d1-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1d2d1-110">Remarks</span></span>  

 <span data-ttu-id="1d2d1-111">`ICLRDataTarget`Объект реализуется модулем записи приложения отладки.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="1d2d1-112">Реализация зависит от типа представляемого целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="1d2d1-113">Целевой элемент может быть процессом, дампом памяти, удаленным компьютером и т. д.</span><span class="sxs-lookup"><span data-stu-id="1d2d1-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2d1-114">Требования</span><span class="sxs-lookup"><span data-stu-id="1d2d1-114">Requirements</span></span>  

 <span data-ttu-id="1d2d1-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d2d1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2d1-116">**Заголовок:** Клрдата. idl</span><span class="sxs-lookup"><span data-stu-id="1d2d1-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="1d2d1-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d2d1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d2d1-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2d1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2d1-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1d2d1-119">See also</span></span>

- [<span data-ttu-id="1d2d1-120">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="1d2d1-120">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
