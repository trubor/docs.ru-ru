---
description: Дополнительные сведения о функции Жетрекуестедрунтимеверсионфорклсид
title: Функция GetRequestedRuntimeVersionForCLSID
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 10fdc947181d3f1fa12b33f11cf31b68fc4285cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785267"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="f9ad9-103">Функция GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="f9ad9-103">GetRequestedRuntimeVersionForCLSID Function</span></span>

<span data-ttu-id="f9ad9-104">Возвращает соответствующую информацию о версии среды CLR для класса с указанным `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="f9ad9-104">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="f9ad9-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ad9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9ad9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9ad9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f9ad9-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="f9ad9-108">окне  `CLSID` Компонента.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-108">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f9ad9-109">заполняет  Буфер, содержащий строку номера версии после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-109">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f9ad9-110">окне  Размер буфера в расширенных символах `pVersion` .</span><span class="sxs-lookup"><span data-stu-id="f9ad9-110">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f9ad9-111">заполняет Длина возвращенного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-111">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="f9ad9-112">окне  Одно из значений CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-112">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="f9ad9-113">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-113">The following values are supported:</span></span>  
  
- <span data-ttu-id="f9ad9-114">CLSID_RESOLUTION_DEFAULT: (0x0) указывает, что следует использовать режим взаимодействия по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-114">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="f9ad9-115">CLSID_RESOLUTION_REGISTERED: (0x1) указывает, что необходимо выполнять поиск в реестре и применять политику оболочки совместимости.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-115">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9ad9-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f9ad9-116">Return Value</span></span>  
  
|<span data-ttu-id="f9ad9-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9ad9-117">HRESULT</span></span>|<span data-ttu-id="f9ad9-118">Описание:</span><span class="sxs-lookup"><span data-stu-id="f9ad9-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9ad9-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9ad9-119">S_OK</span></span>|<span data-ttu-id="f9ad9-120">Функция возвращена успешно.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-120">The function returned successfully.</span></span>|  
|<span data-ttu-id="f9ad9-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9ad9-121">E_INVALIDARG</span></span>|<span data-ttu-id="f9ad9-122">Один из параметров имеет недопустимый тип или формат.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-122">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="f9ad9-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f9ad9-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f9ad9-124">`pVersion`Буфер недостаточно велик для размещения всей строки версии.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-124">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="f9ad9-125">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="f9ad9-125">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="f9ad9-126">Отсутствует класс, зарегистрированный в указанном классе `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="f9ad9-126">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="f9ad9-127">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f9ad9-127">E_POINTER</span></span>|<span data-ttu-id="f9ad9-128">`dwLength` параметр имеет значение null или `cchBuffer` достаточно велик для хранения строки версии, но `pVersion` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="f9ad9-128">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9ad9-129">Требования</span><span class="sxs-lookup"><span data-stu-id="f9ad9-129">Requirements</span></span>  

 <span data-ttu-id="f9ad9-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ad9-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ad9-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9ad9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9ad9-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ad9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ad9-133">См. также</span><span class="sxs-lookup"><span data-stu-id="f9ad9-133">See also</span></span>

- [<span data-ttu-id="f9ad9-134">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="f9ad9-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
