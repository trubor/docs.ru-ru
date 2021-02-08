---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетпинвокемап'
title: Метод IMetaDataEmit::SetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: e50f06385b599a99454da0a9b971b00806d3140a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771851"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="04a0c-103">Метод IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="04a0c-103">IMetaDataEmit::SetPinvokeMap Method</span></span>

<span data-ttu-id="04a0c-104">Задает или изменяет функции сигнатуры PInvoke метода, как определено в предыдущем вызове [IMetaDataEmit::D ефинепинвокемап](imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="04a0c-104">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a0c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04a0c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04a0c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="04a0c-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="04a0c-107">окне Объект, `mdToken` к которому применяются сведения о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="04a0c-107">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="04a0c-108">окне Флаги, используемые PInvoke для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="04a0c-108">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="04a0c-109">Это битовая маска `CorPinvokeMap` значений.</span><span class="sxs-lookup"><span data-stu-id="04a0c-109">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="04a0c-110">окне Имя целевого экспорта в собственной библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="04a0c-110">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="04a0c-111">окне `mdModuleRef` Маркер для целевой неуправляемой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="04a0c-111">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a0c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="04a0c-112">Requirements</span></span>  

 <span data-ttu-id="04a0c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a0c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a0c-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="04a0c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04a0c-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04a0c-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04a0c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a0c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="04a0c-117">See also</span></span>

- [<span data-ttu-id="04a0c-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="04a0c-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="04a0c-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="04a0c-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
