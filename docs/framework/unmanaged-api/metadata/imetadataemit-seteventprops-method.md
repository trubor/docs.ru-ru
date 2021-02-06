---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: SetEventProps'
title: Метод IMetaDataEmit::SetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 888999bc0f80e82e0d139eecac7152a94104ed7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658130"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="4fa5e-103">Метод IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="4fa5e-103">IMetaDataEmit::SetEventProps Method</span></span>

<span data-ttu-id="4fa5e-104">Задает или обновляет указанную функцию события, определенного при предыдущем вызове метода [IMetaDataEmit::D ефинивент](imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="4fa5e-104">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa5e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4fa5e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fa5e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4fa5e-106">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="4fa5e-107">окне Токен события.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-107">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="4fa5e-108">окне Флаги событий.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-108">[in] Event flags.</span></span> <span data-ttu-id="4fa5e-109">Это битовая маска `CorEventAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-109">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="4fa5e-110">окне Токен для класса событий.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-110">[in] The token for the event class.</span></span> <span data-ttu-id="4fa5e-111">Это либо маркер, либо `mdTypeDef` `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="4fa5e-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="4fa5e-112">окне Метод, используемый для подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="4fa5e-113">окне Метод, используемый для отмены подписки на событие или значение null.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="4fa5e-114">окне Метод, используемый (производным классом) для вызова события.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="4fa5e-115">окне Массив токенов для других методов, связанных с событием.</span><span class="sxs-lookup"><span data-stu-id="4fa5e-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="4fa5e-116">Последний элемент массива должен быть `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="4fa5e-116">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa5e-117">Требования</span><span class="sxs-lookup"><span data-stu-id="4fa5e-117">Requirements</span></span>  

 <span data-ttu-id="4fa5e-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa5e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa5e-119">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4fa5e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fa5e-120">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fa5e-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fa5e-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa5e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa5e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="4fa5e-122">See also</span></span>

- [<span data-ttu-id="4fa5e-123">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4fa5e-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4fa5e-124">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4fa5e-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
