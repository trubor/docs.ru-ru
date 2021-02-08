---
description: 'Дополнительные сведения о методе: ICorPublishProcess:: DisplayName'
title: Метод ICorPublishProcess::GetDisplayName
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: 7aef55a40c24953766377f21e8291bceb1594480
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794589"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="bf022-103">Метод ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="bf022-103">ICorPublishProcess::GetDisplayName Method</span></span>

<span data-ttu-id="bf022-104">Возвращает полный путь к исполняемому файлу для процесса, на который ссылается этот [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bf022-104">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf022-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf022-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf022-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bf022-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="bf022-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="bf022-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bf022-108">заполняет Число расширенных символов, возвращаемых в `szName` массиве.</span><span class="sxs-lookup"><span data-stu-id="bf022-108">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="bf022-109">заполняет Массив для хранения имени исполняемого файла, включая полный путь к нему.</span><span class="sxs-lookup"><span data-stu-id="bf022-109">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="bf022-110">Имя заканчивается нулем.</span><span class="sxs-lookup"><span data-stu-id="bf022-110">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf022-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bf022-111">Requirements</span></span>  

 <span data-ttu-id="bf022-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf022-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf022-113">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="bf022-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bf022-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf022-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf022-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf022-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf022-116">См. также</span><span class="sxs-lookup"><span data-stu-id="bf022-116">See also</span></span>

- [<span data-ttu-id="bf022-117">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="bf022-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
