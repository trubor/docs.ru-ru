---
description: Дополнительные сведения о функции CLRDataCreateInstance
title: Функция CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- DLLExport
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 923b0c687d2b337eacb475973927452e3b47ad0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747261"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="754ac-103">Функция CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="754ac-103">CLRDataCreateInstance Function</span></span>

<span data-ttu-id="754ac-104">Создает объект интерфейса для указанного целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="754ac-104">Creates an interface object for the specified target item.</span></span>

## <a name="syntax"></a><span data-ttu-id="754ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="754ac-105">Syntax</span></span>

```cpp
HRESULT CLRDataCreateInstance (
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="754ac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="754ac-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="754ac-107">окне Идентификатор интерфейса, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="754ac-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="754ac-108">окне Указатель на реализуемый пользователем объект [ICLRDataTarget](iclrdatatarget-interface.md) , представляющий целевой элемент, для которого создается объект интерфейса.</span><span class="sxs-lookup"><span data-stu-id="754ac-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="754ac-109">заполняет Указатель на адрес возвращенного объекта интерфейса.</span><span class="sxs-lookup"><span data-stu-id="754ac-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="754ac-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="754ac-110">Remarks</span></span>  

 <span data-ttu-id="754ac-111">`ICLRDataTarget`Объект реализуется модулем записи приложения отладки.</span><span class="sxs-lookup"><span data-stu-id="754ac-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="754ac-112">Реализация зависит от типа представляемого целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="754ac-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="754ac-113">Целевой элемент может быть процессом, дампом памяти, удаленным компьютером и т. д.</span><span class="sxs-lookup"><span data-stu-id="754ac-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754ac-114">Требования</span><span class="sxs-lookup"><span data-stu-id="754ac-114">Requirements</span></span>  

 <span data-ttu-id="754ac-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="754ac-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="754ac-116">**Заголовок:** Клрдата. idl</span><span class="sxs-lookup"><span data-stu-id="754ac-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="754ac-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="754ac-117">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="754ac-118">**Сборка**: mscordacwks.dll, mscordbi.dll</span><span class="sxs-lookup"><span data-stu-id="754ac-118">**Assembly**: mscordacwks.dll, mscordbi.dll</span></span>
  
 <span data-ttu-id="754ac-119">**Платформа .NET Framework версии:** Доступно с момента платформа .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="754ac-119">**.NET Framework Versions:** Available since .NET Framework 2.0</span></span>
  
## <a name="see-also"></a><span data-ttu-id="754ac-120">См. также</span><span class="sxs-lookup"><span data-stu-id="754ac-120">See also</span></span>

- [<span data-ttu-id="754ac-121">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="754ac-121">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
