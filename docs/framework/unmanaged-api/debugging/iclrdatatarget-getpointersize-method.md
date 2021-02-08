---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: GetPointerSize'
title: Метод ICLRDataTarget::GetPointerSize
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: 4c6e5ab9b919d1c5d2d6e2267a48d46a11cccc09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801336"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="64bc6-103">Метод ICLRDataTarget::GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="64bc6-103">ICLRDataTarget::GetPointerSize Method</span></span>

<span data-ttu-id="64bc6-104">Возвращает размер (в байтах) типа указателя, используемого целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="64bc6-104">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="64bc6-105">Этот метод вызывается службами доступа к данным среды CLR.</span><span class="sxs-lookup"><span data-stu-id="64bc6-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64bc6-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64bc6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64bc6-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="64bc6-107">Parameters</span></span>  

 `pointerSize`  
 <span data-ttu-id="64bc6-108">заполняет Указатель на целочисленное значение, указывающее размер (в байтах) указателя на целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="64bc6-108">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64bc6-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="64bc6-109">Remarks</span></span>  

 <span data-ttu-id="64bc6-110">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="64bc6-110">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64bc6-111">Требования</span><span class="sxs-lookup"><span data-stu-id="64bc6-111">Requirements</span></span>  

 <span data-ttu-id="64bc6-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64bc6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64bc6-113">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="64bc6-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="64bc6-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64bc6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64bc6-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64bc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64bc6-116">См. также</span><span class="sxs-lookup"><span data-stu-id="64bc6-116">See also</span></span>

- [<span data-ttu-id="64bc6-117">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="64bc6-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
