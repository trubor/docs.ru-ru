---
description: Дополнительные сведения о функции Креатеаппликатионконтекст
title: Функция CreateApplicationContext
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: f192e1ccc371cb6d50e4a41a286c412825ee4181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761187"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="daea9-103">Функция CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="daea9-103">CreateApplicationContext Function</span></span>

<span data-ttu-id="daea9-104">Эта функция поддерживает платформа .NET Frameworkную инфраструктуру и не предназначена для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="daea9-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daea9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="daea9-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="daea9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="daea9-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="daea9-107">окне Указатель на понятное имя.</span><span class="sxs-lookup"><span data-stu-id="daea9-107">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="daea9-108">заполняет Указатель на контекст приложения.</span><span class="sxs-lookup"><span data-stu-id="daea9-108">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daea9-109">Требования</span><span class="sxs-lookup"><span data-stu-id="daea9-109">Requirements</span></span>  

 <span data-ttu-id="daea9-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daea9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daea9-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="daea9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="daea9-112">**Библиотека:** Включается в качестве ресурса в Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="daea9-112">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="daea9-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daea9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daea9-114">См. также</span><span class="sxs-lookup"><span data-stu-id="daea9-114">See also</span></span>

- [<span data-ttu-id="daea9-115">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="daea9-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="daea9-116">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="daea9-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="daea9-117">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="daea9-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
