---
description: 'Дополнительные сведения о методе ICeeGen:: Емитстринг'
title: Метод ICeeGen::EmitString
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: fca388d044603f932bf90a176cada6e830284702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707115"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="14bc1-103">Метод ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="14bc1-103">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="14bc1-104">Порождает указанную строку в базу кода.</span><span class="sxs-lookup"><span data-stu-id="14bc1-104">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="14bc1-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="14bc1-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bc1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14bc1-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14bc1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="14bc1-107">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="14bc1-108">окне Строка для выдачи.</span><span class="sxs-lookup"><span data-stu-id="14bc1-108">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="14bc1-109">заполняет Относительный виртуальный адрес порожденной строки.</span><span class="sxs-lookup"><span data-stu-id="14bc1-109">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14bc1-110">Требования</span><span class="sxs-lookup"><span data-stu-id="14bc1-110">Requirements</span></span>  

 <span data-ttu-id="14bc1-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bc1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14bc1-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="14bc1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14bc1-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14bc1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14bc1-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14bc1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bc1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="14bc1-115">See also</span></span>

- [<span data-ttu-id="14bc1-116">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="14bc1-116">ICeeGen Interface</span></span>](iceegen-interface.md)
