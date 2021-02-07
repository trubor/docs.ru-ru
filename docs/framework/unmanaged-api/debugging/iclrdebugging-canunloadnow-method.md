---
description: 'Дополнительные сведения о методе: ICLRDebugging:: CanUnloadNow'
title: Метод ICLRDebugging::CanUnloadNow
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 537494fe862c58aa8a8768dd5ce2abc8ca94f87d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723378"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="0602e-103">Метод ICLRDebugging::CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="0602e-103">ICLRDebugging::CanUnloadNow Method</span></span>

<span data-ttu-id="0602e-104">Определяет, используется ли по-прежнему Библиотека, предоставленная интерфейсом [иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md) , или она может быть выгружена.</span><span class="sxs-lookup"><span data-stu-id="0602e-104">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0602e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0602e-105">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0602e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0602e-106">Parameters</span></span>  

 `hmodule`  
 <span data-ttu-id="0602e-107">окне Базовый адрес модуля в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="0602e-107">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0602e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0602e-108">Return Value</span></span>  

 <span data-ttu-id="0602e-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="0602e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0602e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0602e-110">HRESULT</span></span>|<span data-ttu-id="0602e-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="0602e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0602e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0602e-112">S_OK</span></span>|<span data-ttu-id="0602e-113">Модуль, на который указывает ссылка, `hmodule` может быть выгружен.</span><span class="sxs-lookup"><span data-stu-id="0602e-113">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="0602e-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0602e-114">S_FALSE</span></span>|<span data-ttu-id="0602e-115">Модуль, на который ссылается, по `hmodule` -прежнему используется.</span><span class="sxs-lookup"><span data-stu-id="0602e-115">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="0602e-116">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="0602e-116">COR_E_NOT_CLR</span></span>|<span data-ttu-id="0602e-117">Указанный модуль не является модулем CLR.</span><span class="sxs-lookup"><span data-stu-id="0602e-117">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0602e-118">Исключения</span><span class="sxs-lookup"><span data-stu-id="0602e-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0602e-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="0602e-119">Remarks</span></span>  

 <span data-ttu-id="0602e-120">Этот метод проверяет, освобождаются ли все экземпляры `ICorDebug*` интерфейсов, и пока нет потоков в вызове метода [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0602e-120">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0602e-121">Требования</span><span class="sxs-lookup"><span data-stu-id="0602e-121">Requirements</span></span>  

 <span data-ttu-id="0602e-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0602e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0602e-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0602e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0602e-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0602e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0602e-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0602e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0602e-126">См. также</span><span class="sxs-lookup"><span data-stu-id="0602e-126">See also</span></span>

- [<span data-ttu-id="0602e-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0602e-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0602e-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="0602e-128">Debugging</span></span>](index.md)
