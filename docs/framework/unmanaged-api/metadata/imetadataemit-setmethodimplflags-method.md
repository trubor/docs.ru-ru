---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетмесодимплфлагс'
title: Метод IMetaDataEmit::SetMethodImplFlags
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: ea7f3122a21c8651014e60de3629db87eeaf6260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657841"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="4abb5-103">Метод IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="4abb5-103">IMetaDataEmit::SetMethodImplFlags Method</span></span>

<span data-ttu-id="4abb5-104">Задает или обновляет сигнатуру метаданных реализации унаследованного метода, на которую ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="4abb5-104">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4abb5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4abb5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4abb5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4abb5-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="4abb5-107">окне Токен для изменяемого метода.</span><span class="sxs-lookup"><span data-stu-id="4abb5-107">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="4abb5-108">окне Сочетание значений перечисления [кормесодимпл](cormethodimpl-enumeration.md) , определяющих функции реализации метода.</span><span class="sxs-lookup"><span data-stu-id="4abb5-108">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4abb5-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4abb5-109">Requirements</span></span>  

 <span data-ttu-id="4abb5-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4abb5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4abb5-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4abb5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4abb5-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4abb5-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4abb5-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4abb5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abb5-114">См. также</span><span class="sxs-lookup"><span data-stu-id="4abb5-114">See also</span></span>

- [<span data-ttu-id="4abb5-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4abb5-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4abb5-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4abb5-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
