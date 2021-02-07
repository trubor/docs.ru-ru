---
description: 'Дополнительные сведения о методе: Икордебугметадаталокатор:: with MetaData'
title: Метод ICorDebugMetaDataLocator::GetMetaData
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 419a03e42a54057ab70e31a368e918612f3a85f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691696"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="96713-103">Метод ICorDebugMetaDataLocator::GetMetaData</span><span class="sxs-lookup"><span data-stu-id="96713-103">ICorDebugMetaDataLocator::GetMetaData Method</span></span>

<span data-ttu-id="96713-104">Запрашивает у отладчика возврат полного пути к модулю, метаданные которого необходимы для завершения запрошенной отладчиком операции.</span><span class="sxs-lookup"><span data-stu-id="96713-104">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96713-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96713-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="96713-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96713-106">Parameters</span></span>  

 `wszImagePath`  
 <span data-ttu-id="96713-107">[in] Завершающаяся нулевым байтом строка, представляющая полный путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="96713-107">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="96713-108">Если полный путь недоступен, имя и расширение файла (*filename*.*расширение*).</span><span class="sxs-lookup"><span data-stu-id="96713-108">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="96713-109">[in] Временная метка из заголовков PE-файла образа.</span><span class="sxs-lookup"><span data-stu-id="96713-109">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="96713-110">Этот параметр потенциально может использоваться для поиска сервера символов ([SymSrv](/windows/desktop/debug/using-symsrv)).</span><span class="sxs-lookup"><span data-stu-id="96713-110">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="96713-111">[in] Размер образа из заголовков PE-файла.</span><span class="sxs-lookup"><span data-stu-id="96713-111">[in] The image size from PE file headers.</span></span> <span data-ttu-id="96713-112">Этот параметр может использоваться для поиска SymSrv.</span><span class="sxs-lookup"><span data-stu-id="96713-112">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="96713-113">[in] Количество символов в `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="96713-113">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="96713-114">[out] Количество `WCHAR`, записанных в `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="96713-114">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="96713-115">Если метод возвращает E_NOT_SUFFICIENT_BUFFER, содержит число `WCHAR`, необходимых для сохранения пути.</span><span class="sxs-lookup"><span data-stu-id="96713-115">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="96713-116">[out] Указатель на буфер, в который отладчик будет копировать полный путь к файлу, содержащему запрошенные метаданные.</span><span class="sxs-lookup"><span data-stu-id="96713-116">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="96713-117">`ofReadOnly`Флаг из перечисления [коропенфлагс](../metadata/coropenflags-enumeration.md) используется для запроса доступа только для чтения к метаданным в этом файле.</span><span class="sxs-lookup"><span data-stu-id="96713-117">The `ofReadOnly` flag from the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96713-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="96713-118">Return Value</span></span>  

 <span data-ttu-id="96713-119">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="96713-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="96713-120">Все остальные ошибочные значения HRESULT указывают, что файл не удается найти.</span><span class="sxs-lookup"><span data-stu-id="96713-120">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="96713-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96713-121">HRESULT</span></span>|<span data-ttu-id="96713-122">Описание:</span><span class="sxs-lookup"><span data-stu-id="96713-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96713-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="96713-123">S_OK</span></span>|<span data-ttu-id="96713-124">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="96713-124">The method completed successfully.</span></span> <span data-ttu-id="96713-125">`wszPathBuffer` содержит полный путь к файлу и завершается нулевым байтом.</span><span class="sxs-lookup"><span data-stu-id="96713-125">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="96713-126">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="96713-126">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="96713-127">Текущий размер `wszPathBuffer` недостаточен для хранения полного пути.</span><span class="sxs-lookup"><span data-stu-id="96713-127">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="96713-128">В этом случае `pcchPathBuffer` содержит необходимое количество `WCHAR`, включая завершающий символ null, и `GetMetaData` вызывается второй раз с запрошенным размером буфера.</span><span class="sxs-lookup"><span data-stu-id="96713-128">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96713-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="96713-129">Remarks</span></span>  

 <span data-ttu-id="96713-130">Если `wszImagePath` содержит полный путь для модуля из дампа, он указывает путь с компьютера, на котором был создан дамп.</span><span class="sxs-lookup"><span data-stu-id="96713-130">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="96713-131">Файл может не существовать в этом расположении, или по этому пути может храниться неправильный файл с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="96713-131">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96713-132">Требования</span><span class="sxs-lookup"><span data-stu-id="96713-132">Requirements</span></span>  

 <span data-ttu-id="96713-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96713-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96713-134">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96713-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96713-135">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96713-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96713-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96713-136">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96713-137">См. также</span><span class="sxs-lookup"><span data-stu-id="96713-137">See also</span></span>

- [<span data-ttu-id="96713-138">Интерфейс ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="96713-138">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="96713-139">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="96713-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="96713-140">Отладка</span><span class="sxs-lookup"><span data-stu-id="96713-140">Debugging</span></span>](index.md)
