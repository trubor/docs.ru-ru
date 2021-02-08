---
description: Дополнительные сведения о функции Жетрекуестедрунтимеверсион
title: Функция GetRequestedRuntimeVersion
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 836cc4b875ddc427c6779950f5b68d2df8b6ef75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785280"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="b520a-103">Функция GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="b520a-103">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="b520a-104">Возвращает номер версии общеязыковой среды выполнения (CLR), запрошенной указанным приложением.</span><span class="sxs-lookup"><span data-stu-id="b520a-104">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="b520a-105">Если эта версия не установлена, возвращает последнюю версию, установленную до запрошенной версии.</span><span class="sxs-lookup"><span data-stu-id="b520a-105">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="b520a-106">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b520a-106">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b520a-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b520a-107">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b520a-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="b520a-108">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="b520a-109">окне Имя приложения.</span><span class="sxs-lookup"><span data-stu-id="b520a-109">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="b520a-110">заполняет Буфер, содержащий строку номера версии после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="b520a-110">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b520a-111">окне Длина буфера версии.</span><span class="sxs-lookup"><span data-stu-id="b520a-111">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="b520a-112">заполняет Указатель на длину строки номера версии.</span><span class="sxs-lookup"><span data-stu-id="b520a-112">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b520a-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b520a-113">Return Value</span></span>  

 <span data-ttu-id="b520a-114">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="b520a-114">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="b520a-115">Код возврата</span><span class="sxs-lookup"><span data-stu-id="b520a-115">Return code</span></span>|<span data-ttu-id="b520a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b520a-116">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b520a-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b520a-117">S_OK</span></span>|<span data-ttu-id="b520a-118">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="b520a-118">The method completed successfully.</span></span>|  
|<span data-ttu-id="b520a-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b520a-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b520a-120">Буфер версии недостаточно велик для хранения строки версии.</span><span class="sxs-lookup"><span data-stu-id="b520a-120">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="b520a-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b520a-121">E_POINTER</span></span>|<span data-ttu-id="b520a-122">Параметр `pdwLength` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="b520a-122">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b520a-123">Требования</span><span class="sxs-lookup"><span data-stu-id="b520a-123">Requirements</span></span>  

 <span data-ttu-id="b520a-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b520a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b520a-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b520a-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b520a-126">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b520a-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b520a-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b520a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b520a-128">См. также</span><span class="sxs-lookup"><span data-stu-id="b520a-128">See also</span></span>

- [<span data-ttu-id="b520a-129">Функция GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="b520a-129">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="b520a-130">Функция GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="b520a-130">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="b520a-131">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="b520a-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
