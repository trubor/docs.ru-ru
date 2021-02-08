---
description: Дополнительные сведения о функции Клосеклренумератион
title: Функция CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 7669332cc23b78afbb3bf597e7d208a5f707aae5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772774"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="c3ac8-103">Функция CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="c3ac8-103">CloseCLREnumeration Function</span></span>

<span data-ttu-id="c3ac8-104">Закрывает все допустимые события продолжения запуска среды CLR, расположенные в массиве дескрипторов, возвращаемых [функцией EnumerateCLRs](enumerateclrs-function.md), и освобождает память для массивов дескрипторов и строковых путей.</span><span class="sxs-lookup"><span data-stu-id="c3ac8-104">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ac8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3ac8-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ac8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c3ac8-106">Parameters</span></span>  

 `pHandleArray`  
 <span data-ttu-id="c3ac8-107">окне Указатель на массив дескрипторов событий, возвращаемых [функцией EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="c3ac8-107">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="c3ac8-108">окне Указатель на массив строковых путей среды CLR, возвращенных [функцией EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="c3ac8-108">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="c3ac8-109">[in] Значение DWORD, содержащее размер (длину) массива `pHandleArray` или `pStringArray` (они одинаковые).</span><span class="sxs-lookup"><span data-stu-id="c3ac8-109">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3ac8-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c3ac8-110">Return Value</span></span>  

 <span data-ttu-id="c3ac8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3ac8-111">S_OK</span></span>  
 <span data-ttu-id="c3ac8-112">Дескрипторы, открытые [функцией EnumerateCLRs](enumerateclrs-function.md) , закрываются, а память, выделенная для дескрипторов и массивов строк, освобождается.</span><span class="sxs-lookup"><span data-stu-id="c3ac8-112">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="c3ac8-113">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3ac8-113">E_INVALIDARG</span></span>  
 <span data-ttu-id="c3ac8-114">Длина массива `pHandleArray` не соответствует длине, переданной в `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="c3ac8-114">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="c3ac8-115">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="c3ac8-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c3ac8-116">Функции не удалось освободить память для массивов `pHandleArray` и `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="c3ac8-116">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ac8-117">Требования</span><span class="sxs-lookup"><span data-stu-id="c3ac8-117">Requirements</span></span>  

 <span data-ttu-id="c3ac8-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ac8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ac8-119">**Заголовок:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="c3ac8-119">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c3ac8-120">**Библиотека:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="c3ac8-120">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c3ac8-121">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c3ac8-121">**.NET Framework Versions:** 3.5 SP1</span></span>
