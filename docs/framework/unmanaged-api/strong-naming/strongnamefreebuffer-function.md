---
description: Дополнительные сведения о функции StrongNameFreeBuffer
title: Функция StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: fa1b1d7710a981c5284ee79d551cbf51ede285db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736457"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="3990f-103">Функция StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="3990f-103">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="3990f-104">Освобождает память, выделенную предыдущим вызовом функции строгого имени, такой как [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) или [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="3990f-104">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="3990f-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3990f-105">This function has been deprecated.</span></span> <span data-ttu-id="3990f-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3990f-106">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3990f-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3990f-107">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3990f-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="3990f-108">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="3990f-109">окне Указатель на память для освобождения.</span><span class="sxs-lookup"><span data-stu-id="3990f-109">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3990f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3990f-110">Requirements</span></span>  

 <span data-ttu-id="3990f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3990f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3990f-112">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3990f-112">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3990f-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3990f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3990f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3990f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3990f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="3990f-115">See also</span></span>

- [<span data-ttu-id="3990f-116">Метод StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="3990f-116">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="3990f-117">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3990f-117">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
