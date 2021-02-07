---
description: 'Дополнительные сведения о методе ICeeGen:: Жетсектионблокк'
title: Метод ICeeGen::GetSectionBlock
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: d1a9fdeb35507f9dd6528b581be877049d2a1478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721149"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="26817-103">Метод ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="26817-103">ICeeGen::GetSectionBlock Method</span></span>

<span data-ttu-id="26817-104">Возвращает блок базы кода.</span><span class="sxs-lookup"><span data-stu-id="26817-104">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="26817-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="26817-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26817-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26817-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="26817-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="26817-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="26817-108">окне Раздел, из которого извлекается блок базы кода.</span><span class="sxs-lookup"><span data-stu-id="26817-108">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="26817-109">окне Длина извлекаемого блока.</span><span class="sxs-lookup"><span data-stu-id="26817-109">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="26817-110">окне Байт относительно начала раздела, с которым будет выравняться первый байт блока.</span><span class="sxs-lookup"><span data-stu-id="26817-110">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="26817-111">Это расположение блока в разделе.</span><span class="sxs-lookup"><span data-stu-id="26817-111">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="26817-112">заполняет Указатель на расположение, которое получает адрес полученного блока.</span><span class="sxs-lookup"><span data-stu-id="26817-112">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26817-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="26817-113">Remarks</span></span>  

 <span data-ttu-id="26817-114">Вызывайте `GetSectionBlock` только при наличии особых требований к разделам, которые не обрабатываются другими методами.</span><span class="sxs-lookup"><span data-stu-id="26817-114">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26817-115">Требования</span><span class="sxs-lookup"><span data-stu-id="26817-115">Requirements</span></span>  

 <span data-ttu-id="26817-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26817-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26817-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="26817-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26817-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26817-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26817-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26817-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26817-120">См. также</span><span class="sxs-lookup"><span data-stu-id="26817-120">See also</span></span>

- [<span data-ttu-id="26817-121">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="26817-121">ICeeGen Interface</span></span>](iceegen-interface.md)
