---
description: Дополнительные сведения о функции Пребиндассемблекс
title: Функция PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: e94bd7c335555e8109df60a00cadc76f7e13434b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800010"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="2bbdb-103">Функция PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="2bbdb-103">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="2bbdb-104">Возвращает отображаемое имя после применения политики для сборки.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-104">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="2bbdb-105">Эта функция поддерживает платформа .NET Frameworkную инфраструктуру и не предназначена для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-105">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbdb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2bbdb-106">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bbdb-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="2bbdb-107">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="2bbdb-108">окне Определяет контекст приложения.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-108">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="2bbdb-109">окне Определяет имя сборки.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-109">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="2bbdb-110">окне Определяет родительскую сборку.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-110">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="2bbdb-111">Этот параметр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-111">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="2bbdb-112">окне Определяет версию среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-112">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="2bbdb-113">заполняет Содержит отображаемое имя после применения политики.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-113">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2bbdb-114">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2bbdb-115">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bbdb-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="2bbdb-116">Remarks</span></span>  

 <span data-ttu-id="2bbdb-117">`ppNamePostPolicy`Выходной параметр задается только в том случае, если функция возвращает значение HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-117">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="2bbdb-118">В противном случае — значение null.</span><span class="sxs-lookup"><span data-stu-id="2bbdb-118">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbdb-119">Требования</span><span class="sxs-lookup"><span data-stu-id="2bbdb-119">Requirements</span></span>  

 <span data-ttu-id="2bbdb-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bbdb-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bbdb-121">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2bbdb-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2bbdb-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bbdb-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bbdb-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbdb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbdb-124">См. также</span><span class="sxs-lookup"><span data-stu-id="2bbdb-124">See also</span></span>

- [<span data-ttu-id="2bbdb-125">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="2bbdb-125">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
