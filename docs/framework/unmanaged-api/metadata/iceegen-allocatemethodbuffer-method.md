---
description: 'Дополнительные сведения о методе ICeeGen:: Аллокатемесодбуффер'
title: Метод ICeeGen::AllocateMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: ced5ac8b4fdd89fc41c2c70b68c5b49843a519e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707167"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="0c8fb-103">Метод ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="0c8fb-103">ICeeGen::AllocateMethodBuffer Method</span></span>

<span data-ttu-id="0c8fb-104">Создает буфер указанного размера для метода и получает относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="0c8fb-104">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="0c8fb-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="0c8fb-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8fb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c8fb-106">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8fb-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c8fb-107">Parameters</span></span>  

 `cchBuffer`  
 <span data-ttu-id="0c8fb-108">окне Длина создаваемого буфера.</span><span class="sxs-lookup"><span data-stu-id="0c8fb-108">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0c8fb-109">заполняет Возвращаемый буфер.</span><span class="sxs-lookup"><span data-stu-id="0c8fb-109">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="0c8fb-110">заполняет Относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="0c8fb-110">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8fb-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0c8fb-111">Requirements</span></span>  

 <span data-ttu-id="0c8fb-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8fb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8fb-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0c8fb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c8fb-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c8fb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c8fb-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8fb-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0c8fb-116">See also</span></span>

- [<span data-ttu-id="0c8fb-117">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0c8fb-117">ICeeGen Interface</span></span>](iceegen-interface.md)
