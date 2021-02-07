---
description: 'Дополнительные сведения о методе ICeeGen:: Компутепоинтер'
title: Метод ICeeGen::ComputePointer
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 9319343cc93eae3e4c7b060239d23ad8aeb7d3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721181"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="0fc02-103">Метод ICeeGen::ComputePointer</span><span class="sxs-lookup"><span data-stu-id="0fc02-103">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="0fc02-104">Определяет буфер для указанного раздела кода.</span><span class="sxs-lookup"><span data-stu-id="0fc02-104">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="0fc02-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="0fc02-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc02-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fc02-106">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fc02-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fc02-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="0fc02-108">окне Раздел кода, для которого возвращается буфер.</span><span class="sxs-lookup"><span data-stu-id="0fc02-108">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="0fc02-109">окне Относительный виртуальный адрес метода, для которого необходимо получить указатель.</span><span class="sxs-lookup"><span data-stu-id="0fc02-109">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0fc02-110">заполняет Указатель на возвращаемый буфер.</span><span class="sxs-lookup"><span data-stu-id="0fc02-110">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fc02-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0fc02-111">Requirements</span></span>  

 <span data-ttu-id="0fc02-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fc02-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc02-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0fc02-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fc02-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fc02-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fc02-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc02-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc02-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0fc02-116">See also</span></span>

- [<span data-ttu-id="0fc02-117">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0fc02-117">ICeeGen Interface</span></span>](iceegen-interface.md)
