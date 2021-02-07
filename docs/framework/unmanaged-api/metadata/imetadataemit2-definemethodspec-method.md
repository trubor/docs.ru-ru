---
description: 'Дополнительные сведения о методе: IMetaDataEmit2::D Ефинемесодспек'
title: Метод IMetaDataEmit2::DefineMethodSpec
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 4b5283375ba194a86a83b142b3b2bdc06bfd35da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745740"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="6639d-103">Метод IMetaDataEmit2::DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="6639d-103">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="6639d-104">Создает универсальный экземпляр метода и получает маркер для определения.</span><span class="sxs-lookup"><span data-stu-id="6639d-104">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6639d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6639d-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6639d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6639d-106">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="6639d-107">окне Токен для метода, для которого создается универсальный экземпляр.</span><span class="sxs-lookup"><span data-stu-id="6639d-107">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="6639d-108">Токен должен иметь тип `mdMethodDef` или `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="6639d-108">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6639d-109">окне Указатель на двоичную сигнатуру COM+ метода.</span><span class="sxs-lookup"><span data-stu-id="6639d-109">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="6639d-110">окне Размер (в байтах) `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="6639d-110">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="6639d-111">заполняет Токен для определения сигнатуры метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="6639d-111">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6639d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="6639d-112">Requirements</span></span>  

 <span data-ttu-id="6639d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6639d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6639d-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6639d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6639d-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6639d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6639d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6639d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6639d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6639d-117">See also</span></span>

- [<span data-ttu-id="6639d-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6639d-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="6639d-119">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6639d-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
