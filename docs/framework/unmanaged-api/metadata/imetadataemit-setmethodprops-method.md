---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетмесодпропс'
title: Метод IMetaDataEmit::SetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: edecdc14abb386f8fa4cd70535f2b8c012bdc59f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772111"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="934c2-103">Метод IMetaDataEmit::SetMethodProps</span><span class="sxs-lookup"><span data-stu-id="934c2-103">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="934c2-104">Задает или обновляет компонент, хранящийся по указанному относительному виртуальному адресу метода, определенного в предыдущем вызове [IMetaDataEmit::D ефинемесод](imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="934c2-104">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="934c2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="934c2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="934c2-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="934c2-107">окне Токен для изменяемого метода.</span><span class="sxs-lookup"><span data-stu-id="934c2-107">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="934c2-108">окне Атрибуты элемента.</span><span class="sxs-lookup"><span data-stu-id="934c2-108">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="934c2-109">окне Адрес кода.</span><span class="sxs-lookup"><span data-stu-id="934c2-109">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="934c2-110">окне Флаги реализации для метода.</span><span class="sxs-lookup"><span data-stu-id="934c2-110">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934c2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="934c2-111">Requirements</span></span>  

 <span data-ttu-id="934c2-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934c2-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="934c2-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="934c2-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="934c2-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="934c2-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934c2-116">См. также</span><span class="sxs-lookup"><span data-stu-id="934c2-116">See also</span></span>

- [<span data-ttu-id="934c2-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="934c2-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="934c2-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="934c2-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
