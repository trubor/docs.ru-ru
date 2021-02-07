---
description: Дополнительные сведения о функции _CorExeMain2
title: Функция _CorExeMain2
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: 4629ea2f6c2ba13351c409bc382077eea926b507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717112"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="670ac-103">Функция _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="670ac-103">_CorExeMain2 Function</span></span>

<span data-ttu-id="670ac-104">Выполняет точку входа в указанном коде, сопоставленном с памятью.</span><span class="sxs-lookup"><span data-stu-id="670ac-104">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="670ac-105">Эта функция вызывается загрузчиком операционной системы.</span><span class="sxs-lookup"><span data-stu-id="670ac-105">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670ac-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="670ac-106">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="670ac-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="670ac-107">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="670ac-108">окне Указатель на код, сопоставленный с памятью.</span><span class="sxs-lookup"><span data-stu-id="670ac-108">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="670ac-109">окне Количество элементов, которые `pUnmappedPE` могут храниться.</span><span class="sxs-lookup"><span data-stu-id="670ac-109">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="670ac-110">окне Указатель на имя исполняемого образа.</span><span class="sxs-lookup"><span data-stu-id="670ac-110">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="670ac-111">окне Имя файла загрузчика.</span><span class="sxs-lookup"><span data-stu-id="670ac-111">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="670ac-112">окне Параметры командной строки, если они есть.</span><span class="sxs-lookup"><span data-stu-id="670ac-112">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="670ac-113">Требования</span><span class="sxs-lookup"><span data-stu-id="670ac-113">Requirements</span></span>  

 <span data-ttu-id="670ac-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="670ac-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="670ac-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="670ac-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="670ac-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="670ac-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="670ac-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="670ac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670ac-118">См. также</span><span class="sxs-lookup"><span data-stu-id="670ac-118">See also</span></span>

- [<span data-ttu-id="670ac-119">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="670ac-119">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
