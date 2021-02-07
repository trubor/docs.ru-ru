---
description: Дополнительные сведения о функции Лоадстрингрцекс
title: Функция LoadStringRCEx
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: d3fe4b97014e5093dd8d209a5e27bac4ed7b879f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679924"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="a4247-103">Функция LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="a4247-103">LoadStringRCEx Function</span></span>

<span data-ttu-id="a4247-104">Преобразует значение HRESULT в соответствующее сообщение об ошибке для указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="a4247-104">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="a4247-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a4247-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4247-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4247-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4247-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a4247-107">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="a4247-108">окне Идентификатор языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="a4247-108">[in] A culture identifier.</span></span> <span data-ttu-id="a4247-109">Pass-1 для `lcid` для использования языка и региональных параметров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a4247-109">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="a4247-110">[in] Значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a4247-110">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a4247-111">заполняет Буфер, содержащий сообщение об ошибке после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="a4247-111">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a4247-112">окне Размер буфера сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="a4247-112">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a4247-113">окне Игнорируют.</span><span class="sxs-lookup"><span data-stu-id="a4247-113">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="a4247-114">заполняет Указатель на длину сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="a4247-114">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4247-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a4247-115">Return Value</span></span>  

 <span data-ttu-id="a4247-116">Этот метод возвращает стандартные коды ошибок COM, как определено в файле WinError. h, а также следующие значения.</span><span class="sxs-lookup"><span data-stu-id="a4247-116">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a4247-117">Код возврата</span><span class="sxs-lookup"><span data-stu-id="a4247-117">Return code</span></span>|<span data-ttu-id="a4247-118">Описание</span><span class="sxs-lookup"><span data-stu-id="a4247-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a4247-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4247-119">S_OK</span></span>|<span data-ttu-id="a4247-120">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="a4247-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4247-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4247-121">E_INVALIDARG</span></span>|<span data-ttu-id="a4247-122">`szBuffer` имеет значение null или `iMax` равно нулю (0).</span><span class="sxs-lookup"><span data-stu-id="a4247-122">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4247-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="a4247-123">Remarks</span></span>  

 <span data-ttu-id="a4247-124">Если метод не завершается успешно, `szBuffer` содержит пустую строку.</span><span class="sxs-lookup"><span data-stu-id="a4247-124">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4247-125">Требования</span><span class="sxs-lookup"><span data-stu-id="a4247-125">Requirements</span></span>  

 <span data-ttu-id="a4247-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4247-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4247-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4247-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4247-128">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4247-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4247-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4247-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4247-130">См. также</span><span class="sxs-lookup"><span data-stu-id="a4247-130">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a4247-131">Функция LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="a4247-131">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="a4247-132">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="a4247-132">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
