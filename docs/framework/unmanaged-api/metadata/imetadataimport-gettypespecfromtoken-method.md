---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetTypeSpecFromToken'
title: Метод IMetaDataImport::GetTypeSpecFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: b71f8f856da517b3e5046c20d787a555816fb728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789116"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="7dcff-103">Метод IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="7dcff-103">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="7dcff-104">Возвращает двоичную подпись метаданных для спецификации типа, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="7dcff-104">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dcff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7dcff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dcff-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7dcff-106">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="7dcff-107">окне Токен TypeSpec, связанный с запрошенной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="7dcff-107">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="7dcff-108">заполняет Указатель на сигнатуру двоичных метаданных.</span><span class="sxs-lookup"><span data-stu-id="7dcff-108">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="7dcff-109">заполняет Размер подписи метаданных в байтах.</span><span class="sxs-lookup"><span data-stu-id="7dcff-109">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dcff-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7dcff-110">Return Value</span></span>  

 <span data-ttu-id="7dcff-111">Значение HRESULT, указывающее на успешное выполнение или сбой.</span><span class="sxs-lookup"><span data-stu-id="7dcff-111">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="7dcff-112">Сбои можно проверить с помощью макроса FAILed.</span><span class="sxs-lookup"><span data-stu-id="7dcff-112">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dcff-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7dcff-113">Requirements</span></span>  

 <span data-ttu-id="7dcff-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dcff-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dcff-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7dcff-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dcff-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dcff-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dcff-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dcff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcff-118">См. также</span><span class="sxs-lookup"><span data-stu-id="7dcff-118">See also</span></span>

- [<span data-ttu-id="7dcff-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7dcff-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7dcff-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7dcff-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
