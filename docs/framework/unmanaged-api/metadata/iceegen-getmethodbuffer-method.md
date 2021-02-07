---
description: 'Дополнительные сведения о методе ICeeGen:: Жетмесодбуффер'
title: Метод ICeeGen::GetMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 24811f231b1db6d985753d4f4695f432aa12edc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706946"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="c686b-103">Метод ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="c686b-103">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="c686b-104">Возвращает буфер соответствующего размера для метода по указанному относительному виртуальному адресу.</span><span class="sxs-lookup"><span data-stu-id="c686b-104">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="c686b-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="c686b-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c686b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c686b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c686b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c686b-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="c686b-108">окне Относительный виртуальный адрес метода, для которого возвращается буфер.</span><span class="sxs-lookup"><span data-stu-id="c686b-108">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c686b-109">заполняет Указатель на возвращаемый буфер.</span><span class="sxs-lookup"><span data-stu-id="c686b-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c686b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c686b-110">Requirements</span></span>  

 <span data-ttu-id="c686b-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c686b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c686b-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c686b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c686b-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c686b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c686b-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c686b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c686b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c686b-115">See also</span></span>

- [<span data-ttu-id="c686b-116">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="c686b-116">ICeeGen Interface</span></span>](iceegen-interface.md)
