---
description: Дополнительные сведения о функции StrongNameHashSize
title: Функция StrongNameHashSize
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: 3e6700bfce3ba480814f3837011c5f8f7107bbd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781250"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="f5836-103">Функция StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="f5836-103">StrongNameHashSize Function</span></span>

<span data-ttu-id="f5836-104">Получает размер буфера, необходимый для хэша, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="f5836-104">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="f5836-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="f5836-105">This function has been deprecated.</span></span> <span data-ttu-id="f5836-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f5836-106">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5836-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5836-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5836-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="f5836-108">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="f5836-109">окне Хэш-алгоритм, используемый для вычисления размера буфера.</span><span class="sxs-lookup"><span data-stu-id="f5836-109">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="f5836-110">заполняет Размер возвращенного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="f5836-110">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5836-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f5836-111">Return Value</span></span>  

 <span data-ttu-id="f5836-112">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="f5836-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5836-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5836-113">Remarks</span></span>  

 <span data-ttu-id="f5836-114">Если `StrongNameHashSize` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="f5836-114">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5836-115">Требования</span><span class="sxs-lookup"><span data-stu-id="f5836-115">Requirements</span></span>  

 <span data-ttu-id="f5836-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5836-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5836-117">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f5836-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f5836-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5836-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5836-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5836-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5836-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f5836-120">See also</span></span>

- [<span data-ttu-id="f5836-121">Метод StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="f5836-121">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="f5836-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f5836-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
