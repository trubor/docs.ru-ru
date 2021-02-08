---
description: 'Дополнительные сведения о методе ICeeGen:: Трункатесектион'
title: Метод ICeeGen::TruncateSection
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 074c7d7b4222b5b22f1d9b79169d531cd5544b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784214"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="437b6-103">Метод ICeeGen::TruncateSection</span><span class="sxs-lookup"><span data-stu-id="437b6-103">ICeeGen::TruncateSection Method</span></span>

<span data-ttu-id="437b6-104">Усекает указанный раздел кода на заданную длину.</span><span class="sxs-lookup"><span data-stu-id="437b6-104">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="437b6-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="437b6-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="437b6-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="437b6-106">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="437b6-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="437b6-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="437b6-108">окне Раздел для усечения.</span><span class="sxs-lookup"><span data-stu-id="437b6-108">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="437b6-109">окне Длина усечения раздела в байтах.</span><span class="sxs-lookup"><span data-stu-id="437b6-109">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="437b6-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="437b6-110">Remarks</span></span>  

 <span data-ttu-id="437b6-111">Вызывайте `TruncateSection` только при наличии особых требований к разделам, которые не обрабатываются другими методами.</span><span class="sxs-lookup"><span data-stu-id="437b6-111">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="437b6-112">Требования</span><span class="sxs-lookup"><span data-stu-id="437b6-112">Requirements</span></span>  

 <span data-ttu-id="437b6-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="437b6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="437b6-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="437b6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="437b6-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="437b6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="437b6-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="437b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437b6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="437b6-117">See also</span></span>

- [<span data-ttu-id="437b6-118">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="437b6-118">ICeeGen Interface</span></span>](iceegen-interface.md)
