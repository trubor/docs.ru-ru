---
description: 'Дополнительные сведения о методе: ICorPublishProcess:: Manage'
title: Метод ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 55f620a896efd87c2f154ac68ef2db1a1b0a1ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790507"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="46939-103">Метод ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="46939-103">ICorPublishProcess::IsManaged Method</span></span>

<span data-ttu-id="46939-104">Возвращает значение, указывающее, известно ли для процесса, на который ссылается этот [ICorPublishProcess](icorpublishprocess-interface.md) , управляемый код.</span><span class="sxs-lookup"><span data-stu-id="46939-104">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46939-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46939-105">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46939-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="46939-106">Parameters</span></span>  

 `pbManaged`  
 <span data-ttu-id="46939-107">заполняет Указатель на логическое значение, указывающее, имеет ли процесс управляемый код.</span><span class="sxs-lookup"><span data-stu-id="46939-107">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="46939-108">Значение равно `true` , если процесс имеет управляемый код; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="46939-108">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46939-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="46939-109">Remarks</span></span>  

 <span data-ttu-id="46939-110">Поскольку текущая версия `ICorPublishProcess` разрешает доступ только к процессам, имеющим управляемый код, `IsManaged` всегда возвращает `true` .</span><span class="sxs-lookup"><span data-stu-id="46939-110">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46939-111">Требования</span><span class="sxs-lookup"><span data-stu-id="46939-111">Requirements</span></span>  

 <span data-ttu-id="46939-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46939-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46939-113">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="46939-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="46939-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46939-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46939-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46939-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46939-116">См. также</span><span class="sxs-lookup"><span data-stu-id="46939-116">See also</span></span>

- [<span data-ttu-id="46939-117">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="46939-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
