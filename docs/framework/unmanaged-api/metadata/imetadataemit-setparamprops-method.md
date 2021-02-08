---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетпарампропс'
title: Метод IMetaDataEmit::SetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 35e839b05b3671c6c09f315ac636971c386e766e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772030"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="3e86f-103">Метод IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="3e86f-103">IMetaDataEmit::SetParamProps Method</span></span>

<span data-ttu-id="3e86f-104">Задает или изменяет функции параметра метода, который был определен при предыдущем вызове [IMetaDataEmit::D ефинепарам](imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e86f-104">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e86f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e86f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e86f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3e86f-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="3e86f-107">окне Токен для целевого параметра.</span><span class="sxs-lookup"><span data-stu-id="3e86f-107">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="3e86f-108">окне Имя параметра в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="3e86f-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="3e86f-109">окне Флаги для параметра.</span><span class="sxs-lookup"><span data-stu-id="3e86f-109">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="3e86f-110">окне ELEMENT_TYPE_ \* для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="3e86f-110">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3e86f-111">окне Постоянное значение для параметра.</span><span class="sxs-lookup"><span data-stu-id="3e86f-111">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="3e86f-112">окне Размер символов (в Юникоде) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="3e86f-112">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e86f-113">Требования</span><span class="sxs-lookup"><span data-stu-id="3e86f-113">Requirements</span></span>  

 <span data-ttu-id="3e86f-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e86f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e86f-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3e86f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e86f-116">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e86f-116">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e86f-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e86f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e86f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="3e86f-118">See also</span></span>

- [<span data-ttu-id="3e86f-119">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3e86f-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3e86f-120">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3e86f-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
