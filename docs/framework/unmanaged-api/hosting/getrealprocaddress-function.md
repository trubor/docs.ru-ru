---
description: Дополнительные сведения о функции Жетреалпрокаддресс
title: Функция GetRealProcAddress
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: b8b3db77d6aef7fae3045a7aa2310c1fadc70e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785319"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="0fddd-103">Функция GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="0fddd-103">GetRealProcAddress Function</span></span>

<span data-ttu-id="0fddd-104">Возвращает адрес указанной функции, которая экспортируется из последней установленной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0fddd-104">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="0fddd-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0fddd-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fddd-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fddd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fddd-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fddd-107">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="0fddd-108">окне Имя функции.</span><span class="sxs-lookup"><span data-stu-id="0fddd-108">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0fddd-109">заполняет Расположение, которое получает указатель на адрес функции.</span><span class="sxs-lookup"><span data-stu-id="0fddd-109">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fddd-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0fddd-110">Return Value</span></span>  

 <span data-ttu-id="0fddd-111">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям, определенным в CorError. h.</span><span class="sxs-lookup"><span data-stu-id="0fddd-111">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="0fddd-112">Код возврата</span><span class="sxs-lookup"><span data-stu-id="0fddd-112">Return code</span></span>|<span data-ttu-id="0fddd-113">Описание</span><span class="sxs-lookup"><span data-stu-id="0fddd-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0fddd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fddd-114">S_OK</span></span>|<span data-ttu-id="0fddd-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="0fddd-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="0fddd-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0fddd-116">E_POINTER</span></span>|<span data-ttu-id="0fddd-117">Недопустимый параметр `ppv`.</span><span class="sxs-lookup"><span data-stu-id="0fddd-117">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="0fddd-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="0fddd-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="0fddd-119">Функция не экспортируется из среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0fddd-119">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fddd-120">Требования</span><span class="sxs-lookup"><span data-stu-id="0fddd-120">Requirements</span></span>  

 <span data-ttu-id="0fddd-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fddd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fddd-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0fddd-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fddd-123">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fddd-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fddd-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fddd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fddd-125">См. также</span><span class="sxs-lookup"><span data-stu-id="0fddd-125">See also</span></span>

- [<span data-ttu-id="0fddd-126">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="0fddd-126">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
