---
description: Дополнительные сведения о функции Креатеицеефилежен
title: Функция CreateICeeFileGen
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 10aefaad4dd1173e4ef55f727371bab508e2d40c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716936"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="0f6b2-103">Функция CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="0f6b2-103">CreateICeeFileGen Function</span></span>

<span data-ttu-id="0f6b2-104">Создает объект [ицеефилежен](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="0f6b2-104">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="0f6b2-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0f6b2-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f6b2-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f6b2-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f6b2-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f6b2-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="0f6b2-108">заполняет Указатель на адрес нового `ICeeFileGen` объекта.</span><span class="sxs-lookup"><span data-stu-id="0f6b2-108">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f6b2-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0f6b2-109">Return Value</span></span>  

 <span data-ttu-id="0f6b2-110">Этот метод возвращает стандартные коды ошибок COM.</span><span class="sxs-lookup"><span data-stu-id="0f6b2-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f6b2-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f6b2-111">Remarks</span></span>  

 <span data-ttu-id="0f6b2-112">`ICeeFileGen`Объект используется для создания переносимых исполняемых (PE) файлов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0f6b2-112">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="0f6b2-113">Вызовите функцию [дестройицеефилежен](destroyiceefilegen-function.md) , чтобы уничтожить `ICeeFileGen` объект после завершения.</span><span class="sxs-lookup"><span data-stu-id="0f6b2-113">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f6b2-114">Требования</span><span class="sxs-lookup"><span data-stu-id="0f6b2-114">Requirements</span></span>  

 <span data-ttu-id="0f6b2-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f6b2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f6b2-116">**Заголовок:** Ицеефилежен. h</span><span class="sxs-lookup"><span data-stu-id="0f6b2-116">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="0f6b2-117">**Библиотека:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="0f6b2-117">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="0f6b2-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f6b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f6b2-119">См. также</span><span class="sxs-lookup"><span data-stu-id="0f6b2-119">See also</span></span>

- [<span data-ttu-id="0f6b2-120">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="0f6b2-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
