---
description: Дополнительные сведения о функции CreateVersionStringFromModule
title: Функция CreateVersionStringFromModule
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
ms.openlocfilehash: 45ae3ec31cf77e4c96e42a58b23e1f52dcf7c54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661549"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="09bb7-103">Функция CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="09bb7-103">CreateVersionStringFromModule Function</span></span>

<span data-ttu-id="09bb7-104">Создает строку версии из пути среды CLR в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="09bb7-104">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09bb7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09bb7-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09bb7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="09bb7-106">Parameters</span></span>  

 `pidDebuggee`  
 <span data-ttu-id="09bb7-107">[in] Идентификатор процесса, в котором загружается целевая среды CLR.</span><span class="sxs-lookup"><span data-stu-id="09bb7-107">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="09bb7-108">[in] Полный или относительный путь к целевой среде CLR, которая загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="09bb7-108">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="09bb7-109">[out] Буфер возврата для хранения строки версии целевой среды CLR.</span><span class="sxs-lookup"><span data-stu-id="09bb7-109">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="09bb7-110">[in] Размер `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-110">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="09bb7-111">[out] Длина строки версии, возвращенной `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-111">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09bb7-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="09bb7-112">Return Value</span></span>  

 <span data-ttu-id="09bb7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="09bb7-113">S_OK</span></span>  
 <span data-ttu-id="09bb7-114">Строка версии для целевой среды CLR успешно возвращена в `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-114">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="09bb7-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="09bb7-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="09bb7-116">Параметр `szModuleName` имеет значение null, либо один из параметров `pBuffer` и `cchBuffer` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="09bb7-116">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="09bb7-117">Оба параметра `pBuffer` и `cchBuffer` должны иметь значение null или не иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="09bb7-117">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="09bb7-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="09bb7-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="09bb7-119">Значение `pdwLength` больше значения `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-119">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="09bb7-120">Это может быть ожидаемым результатом, если вы передали значение null в оба параметра  `pBuffer` и `cchBuffer`, а также запросили необходимый размер буфера с помощью `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-120">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="09bb7-121">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="09bb7-121">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="09bb7-122">Параметр `szModuleName` не содержит путь к допустимой среде CLR в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="09bb7-122">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="09bb7-123">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="09bb7-123">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="09bb7-124">Параметр `pidDebuggee` не ссылается на допустимый процесс, или произошел другой сбой.</span><span class="sxs-lookup"><span data-stu-id="09bb7-124">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09bb7-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="09bb7-125">Remarks</span></span>  

 <span data-ttu-id="09bb7-126">Эта функция принимает процесс CLR, который определяется параметром `pidDebuggee` и строкой пути, заданной параметром `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-126">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="09bb7-127">Строка версии возвращается в буфер, на который указывает `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-127">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="09bb7-128">Эта строка непрозрачна для пользователя функции, то есть сама строка версии не имеет внутреннего смысла.</span><span class="sxs-lookup"><span data-stu-id="09bb7-128">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="09bb7-129">Он используется исключительно в контексте этой функции и [функции CreateDebuggingInterfaceFromVersion](createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="09bb7-129">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="09bb7-130">Эта функция должна вызываться дважды.</span><span class="sxs-lookup"><span data-stu-id="09bb7-130">This function should be called twice.</span></span> <span data-ttu-id="09bb7-131">При первом вызове передайте значение null для обоих параметров `pBuffer` и `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-131">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="09bb7-132">После этого размер буфера, необходимый для `pBuffer`, будет возвращен в `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-132">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="09bb7-133">Затем можно вызвать эту функцию во второй раз и передать буфер в `pBuffer` и его размер в `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="09bb7-133">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09bb7-134">Требования</span><span class="sxs-lookup"><span data-stu-id="09bb7-134">Requirements</span></span>  

 <span data-ttu-id="09bb7-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09bb7-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09bb7-136">**Заголовок:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="09bb7-136">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="09bb7-137">**Библиотека:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="09bb7-137">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="09bb7-138">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="09bb7-138">**.NET Framework Versions:** 3.5 SP1</span></span>
