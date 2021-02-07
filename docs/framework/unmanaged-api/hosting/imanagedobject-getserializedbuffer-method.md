---
description: 'Дополнительные сведения о методе: IManagedObject:: GetSerializedBuffer'
title: Метод IManagedObject::GetSerializedBuffer
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: f324b6ed1e9cea21fec9027a954fbad54174dd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753774"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="39a38-103">Метод IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="39a38-103">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="39a38-104">Возвращает строковое представление этого управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="39a38-104">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39a38-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39a38-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="39a38-106">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="39a38-107">заполняет Указатель на строку, которая является сериализованным объектом.</span><span class="sxs-lookup"><span data-stu-id="39a38-107">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39a38-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="39a38-108">Remarks</span></span>  

 <span data-ttu-id="39a38-109">`GetSerializedBuffer`Метод сериализует объект, чтобы его можно было маршалировать клиенту.</span><span class="sxs-lookup"><span data-stu-id="39a38-109">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39a38-110">Требования</span><span class="sxs-lookup"><span data-stu-id="39a38-110">Requirements</span></span>  

 <span data-ttu-id="39a38-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39a38-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39a38-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="39a38-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39a38-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39a38-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39a38-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39a38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a38-115">См. также</span><span class="sxs-lookup"><span data-stu-id="39a38-115">See also</span></span>

- [<span data-ttu-id="39a38-116">Интерфейс IManagedObject</span><span class="sxs-lookup"><span data-stu-id="39a38-116">IManagedObject Interface</span></span>](imanagedobject-interface.md)
