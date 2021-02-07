---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинемемберреф'
title: Метод IMetaDataEmit::DefineMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 1d88294cea14369c8a8f16b6048f96472fbb9502
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753423"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="0fd7c-103">Метод IMetaDataEmit::DefineMemberRef</span><span class="sxs-lookup"><span data-stu-id="0fd7c-103">IMetaDataEmit::DefineMemberRef Method</span></span>

<span data-ttu-id="0fd7c-104">Определяет ссылку на член модуля вне текущей области и получает маркер для этого эталонного определения.</span><span class="sxs-lookup"><span data-stu-id="0fd7c-104">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd7c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fd7c-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd7c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fd7c-106">Parameters</span></span>  

 `tkImport`  
 <span data-ttu-id="0fd7c-107">окне Токен для класса или интерфейса целевого элемента, если элемент не является глобальным; Если элемент является глобальным, `mdModuleRef` маркер для этого файла.</span><span class="sxs-lookup"><span data-stu-id="0fd7c-107">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="0fd7c-108">окне Имя целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="0fd7c-108">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0fd7c-109">окне Сигнатура целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="0fd7c-109">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0fd7c-110">окне Число байтов в `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="0fd7c-110">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="0fd7c-111">заполняет `mdMemberRef` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="0fd7c-111">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd7c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0fd7c-112">Requirements</span></span>  

 <span data-ttu-id="0fd7c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd7c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd7c-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0fd7c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fd7c-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fd7c-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fd7c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd7c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0fd7c-117">See also</span></span>

- [<span data-ttu-id="0fd7c-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0fd7c-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0fd7c-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0fd7c-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
