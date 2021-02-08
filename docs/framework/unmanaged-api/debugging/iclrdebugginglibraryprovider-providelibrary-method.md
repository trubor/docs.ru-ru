---
description: 'Дополнительные сведения о методе: Иклрдебуггинглибрарипровидер::P Ровиделибрари'
title: Метод ICLRDebuggingLibraryProvider::ProvideLibrary
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 624061fb9b23af7a69616d4565586ac0fd129860
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772626"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="2b2f7-103">Метод ICLRDebuggingLibraryProvider::ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="2b2f7-103">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="2b2f7-104">Возвращает интерфейс обратного вызова поставщика библиотеки, который позволяет находить и загружать библиотеки отладки среды CLR для конкретной версии.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-104">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b2f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b2f7-105">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="2b2f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2b2f7-106">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="2b2f7-107">окне Имя запрашиваемого модуля.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-107">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="2b2f7-108">окне Метка даты и времени, хранящаяся в заголовке COFF файлов PE.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-108">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="2b2f7-109">окне `SizeOfImage` Поле, хранящееся в необязательном заголовке файла PE файлов в формате COFF.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-109">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="2b2f7-110">заполняет Обработчик для запрошенного модуля.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-110">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b2f7-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2b2f7-111">Return Value</span></span>

<span data-ttu-id="2b2f7-112">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="2b2f7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b2f7-113">HRESULT</span></span>|<span data-ttu-id="2b2f7-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="2b2f7-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2b2f7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b2f7-115">S_OK</span></span>|<span data-ttu-id="2b2f7-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-116">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="2b2f7-117">Исключения</span><span class="sxs-lookup"><span data-stu-id="2b2f7-117">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="2b2f7-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="2b2f7-118">Remarks</span></span>

<span data-ttu-id="2b2f7-119">`ProvideLibrary` позволяет отладчику предоставлять модули, необходимые для отладки конкретных файлов среды CLR, таких как mscordbi.dll и mscordacwks.dll.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-119">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="2b2f7-120">Дескрипторы модулей должны оставаться действительными до тех пор, пока вызов метода [ICLRDebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md) не указывает на то, что они могут быть освобождены, и на этом этапе вызывающая сторона обязана освободить дескрипторы.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-120">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="2b2f7-121">Отладчик может использовать любые доступные средства для размещения или получения модуля отладки.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-121">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b2f7-122">Эта функция позволяет вызывающему API предоставлять модули, которые содержат исполняемый и, возможно, вредоносный код.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-122">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="2b2f7-123">В целях обеспечения безопасности вызывающий объект не должен использовать `ProvideLibrary` для распространения кода, который не готов к выполнению.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-123">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="2b2f7-124">При обнаружении серьезной проблемы безопасности в уже выпущенной библиотеке, например mscordbi.dll или mscordacwks.dll, оболочку совместимости можно исправить, чтобы распознать поврежденные версии файлов.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-124">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="2b2f7-125">После этого оболочка совместимости может выдавать запросы на исправленные версии файлов и отклонять поврежденные версии, если они предоставляются в ответ на любой запрос.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-125">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="2b2f7-126">Это может произойти только в том случае, если пользователь установил исправление для новой версии оболочки совместимости.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-126">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="2b2f7-127">Неисправленные версии останутся уязвимыми.</span><span class="sxs-lookup"><span data-stu-id="2b2f7-127">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b2f7-128">Требования</span><span class="sxs-lookup"><span data-stu-id="2b2f7-128">Requirements</span></span>

<span data-ttu-id="2b2f7-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2f7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2b2f7-130">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b2f7-130">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2b2f7-131">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b2f7-131">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2b2f7-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2f7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2f7-133">См. также</span><span class="sxs-lookup"><span data-stu-id="2b2f7-133">See also</span></span>

- [<span data-ttu-id="2b2f7-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2b2f7-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2b2f7-135">Отладка</span><span class="sxs-lookup"><span data-stu-id="2b2f7-135">Debugging</span></span>](index.md)
