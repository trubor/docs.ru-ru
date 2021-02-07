---
description: 'Дополнительные сведения о методе ICeeGen:: Жетсектиондатален'
title: Метод ICeeGen::GetSectionDataLen
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 9475112a6f25e9a4c57c4ded6cd11dab9bf352b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721060"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="55661-103">Метод ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="55661-103">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="55661-104">Возвращает длину указанного раздела.</span><span class="sxs-lookup"><span data-stu-id="55661-104">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="55661-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="55661-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55661-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55661-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55661-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="55661-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="55661-108">окне Раздел данных, длина которого будет получена.</span><span class="sxs-lookup"><span data-stu-id="55661-108">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="55661-109">заполняет Возвращаемая длина указанного раздела.</span><span class="sxs-lookup"><span data-stu-id="55661-109">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55661-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="55661-110">Remarks</span></span>  

 <span data-ttu-id="55661-111">Вызывайте `GetSectionDataLen` только при наличии особых требований к разделам, которые не обрабатываются другими методами.</span><span class="sxs-lookup"><span data-stu-id="55661-111">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55661-112">Требования</span><span class="sxs-lookup"><span data-stu-id="55661-112">Requirements</span></span>  

 <span data-ttu-id="55661-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55661-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55661-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="55661-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55661-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55661-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55661-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55661-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55661-117">См. также</span><span class="sxs-lookup"><span data-stu-id="55661-117">See also</span></span>

- [<span data-ttu-id="55661-118">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="55661-118">ICeeGen Interface</span></span>](iceegen-interface.md)
