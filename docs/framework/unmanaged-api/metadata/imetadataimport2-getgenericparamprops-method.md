---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: Жетженерикпарампропс'
title: Метод IMetaDataImport2::GetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688732"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="60ece-103">Метод IMetaDataImport2::GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="60ece-103">IMetaDataImport2::GetGenericParamProps Method</span></span>

<span data-ttu-id="60ece-104">Возвращает метаданные, связанные с универсальным параметром, представленным указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="60ece-104">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ece-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60ece-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ece-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60ece-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="60ece-107">окне Токен, представляющий универсальный параметр, для которого возвращаются метаданные.</span><span class="sxs-lookup"><span data-stu-id="60ece-107">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="60ece-108">заполняет Порядковый номер `Type` параметра в родительском конструкторе или методе.</span><span class="sxs-lookup"><span data-stu-id="60ece-108">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="60ece-109">заполняет Значение перечисления [корженерикпараматтр](corgenericparamattr-enumeration.md) , описывающее объект `Type` для универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="60ece-109">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="60ece-110">заполняет Токен TypeDef или MethodDef, представляющий владельца параметра.</span><span class="sxs-lookup"><span data-stu-id="60ece-110">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="60ece-111">заполняет Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="60ece-111">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="60ece-112">заполняет Имя универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="60ece-112">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="60ece-113">окне Размер `wzName` буфера.</span><span class="sxs-lookup"><span data-stu-id="60ece-113">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="60ece-114">заполняет Возвращаемый размер имени в расширенных символах.</span><span class="sxs-lookup"><span data-stu-id="60ece-114">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ece-115">Требования</span><span class="sxs-lookup"><span data-stu-id="60ece-115">Requirements</span></span>  

 <span data-ttu-id="60ece-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60ece-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ece-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="60ece-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60ece-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60ece-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60ece-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ece-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ece-120">См. также</span><span class="sxs-lookup"><span data-stu-id="60ece-120">See also</span></span>

- [<span data-ttu-id="60ece-121">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="60ece-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="60ece-122">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="60ece-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
