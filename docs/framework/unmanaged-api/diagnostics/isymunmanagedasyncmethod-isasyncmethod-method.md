---
description: 'Дополнительные сведения о методе: Исимунманажедасинкмесод:: Исасинкмесод'
title: Метод ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 4b151f5367bac5fd92cc8237492cad6dacfb8e88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790260"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="82da9-103">Метод ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="82da9-103">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="82da9-104">Проверяет, имеет ли метод асинхронную информацию.</span><span class="sxs-lookup"><span data-stu-id="82da9-104">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="82da9-105">Если этот метод возвращает значение `FALSE` , то он недопустим для вызова любых других методов в этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="82da9-105">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="82da9-106">`E_UNEXPECTED`В этом случае они будут возвращаться.</span><span class="sxs-lookup"><span data-stu-id="82da9-106">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82da9-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82da9-107">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82da9-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="82da9-108">Parameters</span></span>  
  
|<span data-ttu-id="82da9-109">Параметр</span><span class="sxs-lookup"><span data-stu-id="82da9-109">Parameter</span></span>|<span data-ttu-id="82da9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="82da9-110">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="82da9-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="82da9-111">Return Value</span></span>  

 <span data-ttu-id="82da9-112">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="82da9-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82da9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="82da9-113">Requirements</span></span>  

 <span data-ttu-id="82da9-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="82da9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82da9-115">См. также</span><span class="sxs-lookup"><span data-stu-id="82da9-115">See also</span></span>

- [<span data-ttu-id="82da9-116">Интерфейс ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="82da9-116">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
