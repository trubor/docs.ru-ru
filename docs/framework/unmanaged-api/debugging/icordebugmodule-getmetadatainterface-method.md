---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Жетметадатаинтерфаце'
title: Метод ICorDebugModule::GetMetaDataInterface
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: 39af2560b4c10f6dc490bfba5425e2339a7c1823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691648"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="ed9d8-103">Метод ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="ed9d8-103">ICorDebugModule::GetMetaDataInterface Method</span></span>

<span data-ttu-id="ed9d8-104">Возвращает объект интерфейса метаданных, который может использоваться для проверки метаданных модуля.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-104">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed9d8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed9d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed9d8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ed9d8-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="ed9d8-107">окне Идентификатор ссылки, указывающий интерфейс метаданных.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-107">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="ed9d8-108">заполняет Указатель на адрес `T:IUnknown` объекта, который является одним из [интерфейсов метаданных](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ed9d8-108">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed9d8-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed9d8-109">Remarks</span></span>  

 <span data-ttu-id="ed9d8-110">Отладчик может использовать `GetMetaDataInterface` метод, чтобы создать копию исходных метаданных для модуля, который необходимо сделать для изменения этого модуля.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-110">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="ed9d8-111">Отладчик вызывает метод `GetMetaDataInterface` [IMetaDataEmit:: саветомемори](../metadata/imetadataemit-savetomemory-method.md) , чтобы получить объект интерфейса [IMetaDataEmit](../metadata/imetadataemit-interface.md) для этого модуля, а затем вызывает методические данные класса, чтобы сохранить копию метаданных модуля в памяти.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-111">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed9d8-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ed9d8-112">Requirements</span></span>  

 <span data-ttu-id="ed9d8-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed9d8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed9d8-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed9d8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed9d8-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed9d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed9d8-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed9d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9d8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ed9d8-117">See also</span></span>

- [<span data-ttu-id="ed9d8-118">Метаданные</span><span class="sxs-lookup"><span data-stu-id="ed9d8-118">Metadata</span></span>](../metadata/index.md)
