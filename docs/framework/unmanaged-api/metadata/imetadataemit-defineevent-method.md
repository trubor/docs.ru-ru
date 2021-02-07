---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинивент'
title: Метод IMetaDataEmit::DefineEvent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: f96f3a5b2ed16ba83223312af82cac7688cebfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753475"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="9aa41-103">Метод IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="9aa41-103">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="9aa41-104">Создает определение для события с указанной сигнатурой метаданных и получает маркер для этого определения события.</span><span class="sxs-lookup"><span data-stu-id="9aa41-104">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa41-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9aa41-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aa41-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9aa41-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="9aa41-107">окне Токен для целевого класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9aa41-107">[in] The token for the target class or interface.</span></span> <span data-ttu-id="9aa41-108">Это либо токен, `mdTypeDef` либо `mdTypeDefNil` .</span><span class="sxs-lookup"><span data-stu-id="9aa41-108">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="9aa41-109">[in] Имя события.</span><span class="sxs-lookup"><span data-stu-id="9aa41-109">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="9aa41-110">окне Флаги событий.</span><span class="sxs-lookup"><span data-stu-id="9aa41-110">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="9aa41-111">окне Токен для класса событий.</span><span class="sxs-lookup"><span data-stu-id="9aa41-111">[in] The token for the event class.</span></span> <span data-ttu-id="9aa41-112">Это `mdTypeDef` , `mdTypeRef` или, или `mdTokenNil` маркер.</span><span class="sxs-lookup"><span data-stu-id="9aa41-112">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="9aa41-113">окне Метод, используемый для подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="9aa41-113">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="9aa41-114">окне Метод, используемый для отмены подписки на событие или значение null.</span><span class="sxs-lookup"><span data-stu-id="9aa41-114">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="9aa41-115">окне Метод, используемый (производным классом) для вызова события.</span><span class="sxs-lookup"><span data-stu-id="9aa41-115">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9aa41-116">окне Массив токенов для других методов, связанных с событием.</span><span class="sxs-lookup"><span data-stu-id="9aa41-116">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="9aa41-117">Массив завершается `mdMethodDefNil` токеном.</span><span class="sxs-lookup"><span data-stu-id="9aa41-117">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="9aa41-118">заполняет Маркер метаданных, назначенный событию.</span><span class="sxs-lookup"><span data-stu-id="9aa41-118">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa41-119">Требования</span><span class="sxs-lookup"><span data-stu-id="9aa41-119">Requirements</span></span>  

 <span data-ttu-id="9aa41-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa41-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa41-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="9aa41-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9aa41-122">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9aa41-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aa41-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa41-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa41-124">См. также</span><span class="sxs-lookup"><span data-stu-id="9aa41-124">See also</span></span>

- [<span data-ttu-id="9aa41-125">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9aa41-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9aa41-126">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9aa41-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
