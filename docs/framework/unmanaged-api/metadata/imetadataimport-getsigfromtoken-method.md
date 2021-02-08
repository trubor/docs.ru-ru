---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetSigFromToken'
title: Метод IMetaDataImport::GetSigFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
ms.openlocfilehash: 16b77fe5866319e24b33ec4ce9d2d56797f04514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789142"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="8a32c-103">Метод IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="8a32c-103">IMetaDataImport::GetSigFromToken Method</span></span>

<span data-ttu-id="8a32c-104">Возвращает двоичную подпись метаданных, связанную с указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="8a32c-104">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a32c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a32c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a32c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a32c-106">Parameters</span></span>  

 `mdSig`  
 <span data-ttu-id="8a32c-107">окне Токен, для которого возвращается сигнатура двоичных метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a32c-107">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="8a32c-108">заполняет Указатель на возвращаемую сигнатуру метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a32c-108">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="8a32c-109">заполняет Размер в байтах двоичной подписи метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a32c-109">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a32c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="8a32c-110">Requirements</span></span>  

 <span data-ttu-id="8a32c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a32c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a32c-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8a32c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a32c-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a32c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a32c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a32c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a32c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="8a32c-115">See also</span></span>

- [<span data-ttu-id="8a32c-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8a32c-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8a32c-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8a32c-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
