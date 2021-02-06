---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сесандлер'
title: Метод IMetaDataEmit::SetHandler
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 07ebf8eef816d373e92a82fc84adacfe5a8599fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657883"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="d920e-103">Метод IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="d920e-103">IMetaDataEmit::SetHandler Method</span></span>

<span data-ttu-id="d920e-104">Задает метод, на который ссылается указанный `IUnknown` указатель, в качестве обратного вызова уведомления для повторного сопоставления токена.</span><span class="sxs-lookup"><span data-stu-id="d920e-104">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d920e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d920e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d920e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d920e-106">Parameters</span></span>  

 `pUnk`  
 <span data-ttu-id="d920e-107">окне Регистрируемый обработчик.</span><span class="sxs-lookup"><span data-stu-id="d920e-107">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d920e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d920e-108">Remarks</span></span>  

 <span data-ttu-id="d920e-109">Обработчик метаданных отправляет уведомление с помощью метода, предоставляемого `SetHandler` , компиляторам, которые не создают записи оптимизированным образом и хотели бы оптимизировать сохраненные записи.</span><span class="sxs-lookup"><span data-stu-id="d920e-109">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="d920e-110">Если метод обратного вызова не предоставляется через `SetHandler` , то для сохранения не будет выполняться оптимизация, за исключением случаев, когда для каждой области были объединены несколько областей импорта с использованием `IMapToken` On MERGE.</span><span class="sxs-lookup"><span data-stu-id="d920e-110">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d920e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d920e-111">Requirements</span></span>  

 <span data-ttu-id="d920e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d920e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d920e-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="d920e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d920e-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d920e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d920e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d920e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d920e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d920e-116">See also</span></span>

- [<span data-ttu-id="d920e-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d920e-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d920e-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d920e-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
