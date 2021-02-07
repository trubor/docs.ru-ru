---
description: Дополнительные сведения о функции Лоадстрингрк
title: Функция LoadStringRC
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 188597f9dc21b6a67fb84e91cd66b50ba5a514f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679926"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="f11a1-103">Функция LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="f11a1-103">LoadStringRC Function</span></span>

<span data-ttu-id="f11a1-104">Преобразует значение HRESULT в сообщение об ошибке с помощью языка и региональных параметров по умолчанию текущего потока.</span><span class="sxs-lookup"><span data-stu-id="f11a1-104">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="f11a1-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f11a1-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11a1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f11a1-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f11a1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f11a1-107">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="f11a1-108">[in] Значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f11a1-108">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="f11a1-109">заполняет Буфер, содержащий сообщение об ошибке после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="f11a1-109">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="f11a1-110">окне Размер буфера сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="f11a1-110">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="f11a1-111">окне Игнорируют.</span><span class="sxs-lookup"><span data-stu-id="f11a1-111">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f11a1-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f11a1-112">Return Value</span></span>  

 <span data-ttu-id="f11a1-113">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="f11a1-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f11a1-114">Код возврата</span><span class="sxs-lookup"><span data-stu-id="f11a1-114">Return code</span></span>|<span data-ttu-id="f11a1-115">Описание</span><span class="sxs-lookup"><span data-stu-id="f11a1-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f11a1-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f11a1-116">S_OK</span></span>|<span data-ttu-id="f11a1-117">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f11a1-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="f11a1-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f11a1-118">E_INVALIDARG</span></span>|<span data-ttu-id="f11a1-119">`szBuffer` имеет значение null или `iMax` равно нулю (0).</span><span class="sxs-lookup"><span data-stu-id="f11a1-119">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f11a1-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f11a1-120">Remarks</span></span>  

 <span data-ttu-id="f11a1-121">Если метод не завершается успешно, `szBuffer` содержит пустую строку.</span><span class="sxs-lookup"><span data-stu-id="f11a1-121">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11a1-122">Требования</span><span class="sxs-lookup"><span data-stu-id="f11a1-122">Requirements</span></span>  

 <span data-ttu-id="f11a1-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f11a1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11a1-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f11a1-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f11a1-125">**Библиотека:** MSCorEE.dll и Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="f11a1-125">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f11a1-126">Используйте MSCorEE.dll вместо Mscorwks.dll, чтобы убедиться в правильности целевой версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f11a1-126">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f11a1-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11a1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11a1-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f11a1-128">See also</span></span>

- [<span data-ttu-id="f11a1-129">Функция LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="f11a1-129">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="f11a1-130">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="f11a1-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
