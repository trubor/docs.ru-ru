---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: SetFieldProps'
title: Метод IMetaDataEmit::SetFieldProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: ee9964077e556a1d0666a836ca0c3bab92540252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658013"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="9a206-103">Метод IMetaDataEmit::SetFieldProps</span><span class="sxs-lookup"><span data-stu-id="9a206-103">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="9a206-104">Задает или обновляет значение по умолчанию для поля, на которое ссылается заданный токен поля.</span><span class="sxs-lookup"><span data-stu-id="9a206-104">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a206-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a206-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a206-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9a206-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="9a206-107">окне Токен для целевого поля.</span><span class="sxs-lookup"><span data-stu-id="9a206-107">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="9a206-108">окне Атрибуты поля.</span><span class="sxs-lookup"><span data-stu-id="9a206-108">[in] Field attributes.</span></span> <span data-ttu-id="9a206-109">Это битовая маска `CorFieldAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="9a206-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9a206-110">окне `ELEMENT_TYPE_` *\** Значение для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="9a206-110">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="9a206-111">Это `CorElementType` значение.</span><span class="sxs-lookup"><span data-stu-id="9a206-111">This is a `CorElementType` value.</span></span> <span data-ttu-id="9a206-112">Если константа не определена, присвойте этому параметру значение `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="9a206-112">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9a206-113">окне Постоянное значение для поля.</span><span class="sxs-lookup"><span data-stu-id="9a206-113">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9a206-114">окне Размер (в символах Юникода) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="9a206-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a206-115">Требования</span><span class="sxs-lookup"><span data-stu-id="9a206-115">Requirements</span></span>  

 <span data-ttu-id="9a206-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a206-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a206-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="9a206-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a206-118">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a206-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a206-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a206-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a206-120">См. также</span><span class="sxs-lookup"><span data-stu-id="9a206-120">See also</span></span>

- [<span data-ttu-id="9a206-121">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9a206-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9a206-122">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9a206-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
