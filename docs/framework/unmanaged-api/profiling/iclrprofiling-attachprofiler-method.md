---
description: 'Дополнительные сведения о методе: Иклрпрофилинг:: AttachProfiler'
title: Метод ICLRProfiling::AttachProfiler
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
ms.openlocfilehash: 00ae5ca76462d8800a77c2869ef73703a4f1d980
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760773"
---
# <a name="iclrprofilingattachprofiler-method"></a>Метод ICLRProfiling::AttachProfiler

Подключает указанный профилировщик к указанному процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Параметры

`dwProfileeProcessID` окне Идентификатор процесса, к которому должен быть присоединен профилировщик. На 64-разрядном компьютере разрядность профилируемого процесса должна соответствовать разрядности инициирующего процесса, вызывающего метод `AttachProfiler`. Если учетная запись пользователя, в которой вызывается метод `AttachProfiler`, имеет права администратора, целевым процессом может быть любой процесс в системе. В противном случае целевой процесс должен принадлежать той же учетной записи пользователя.

`dwMillisecondsMax` окне Длительность выполнения (в миллисекундах) `AttachProfiler` . Инициирующий процесс должен передавать интервал времени, которого заведомо будет достаточно, чтобы конкретный профилировщик завершил свою инициализацию.
  
`pClsidProfiler` окне Указатель на идентификатор CLSID загружаемого профилировщика. Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`.

`wszProfilerPath` окне Полный путь к загружаемому файлу DLL профилировщика. Эта строка должна содержать не более 260 символов, включая символ конца строки null. Если в параметре `wszProfilerPath` задана пустая строка или значение null, среда CLR будет пытаться найти местоположение DLL-файла профилировщика путем поиска в реестре CLSID, на который указывает параметр `pClsidProfiler`.

`pvClientData` окне Указатель на данные, передаваемые профилировщику методом [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) . Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`. Если параметр `pvClientData` имеет значение null, параметр `cbClientData` должен иметь значение 0 (ноль).

`cbClientData` окне Размер (в байтах) данных, на которые `pvClientData` указывает.

## <a name="return-value"></a>Возвращаемое значение  

 Этот метод возвращает следующие значения HRESULT.  
  
|HRESULT|Описание:|  
|-------------|-----------------|  
|S_OK|Указанный профилировщик успешно подключен к целевому процессу.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Уже существует активный профилировщик или профилировщик, подключенный к целевому процессу.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Указанный профилировщик не поддерживает подключение. Инициирующий процесс может попытаться подключить другой профилировщик.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Не удалось запросить подключение профилировщика, так как версия целевого процесса несовместима с текущим процессом, вызывающим метод `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Пользователь инициирующего процесса не имеет доступа к целевому процессу.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Пользователь инициирующего процесса не имеет привилегий, необходимых для подключения профилировщика к указанному целевому процессу. В журнале событий приложений могут содержаться дополнительные сведения.|  
|CORPROF_E_IPC_FAILED|Произошла ошибка при взаимодействии с целевым процессом. Обычно это происходит при завершении работы целевого процесса.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Целевой процесс не существует, или в нем не запущена среда CLR, которая поддерживает подключение. Это может указывать, что среда CLR была выгружена после вызова метода перечисления среды выполнения.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Время ожидания истекло, а загрузка профилировщика не началась. Можно повторить операцию подключения. Время ожидания истекает, когда метод завершения в целевом процессе выполняется дольше, чем задано в значении времени ожидания.|  
|E_INVALIDARG|Как минимум один из следующих параметров имеет недопустимое значение.|  
|E_FAIL|Произошел другой, не указанный сбой.|  
|Другие коды ошибок|Если метод [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) профилировщика ВОЗВРАЩАЕТ значение HRESULT, которое указывает на сбой, `AttachProfiler` ВОЗВРАЩАЕТ то же значение HRESULT. В этом случае E_NOTIMPL преобразуется в CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="memory-management"></a>Управление памятью  

 В соответствии с соглашениями COM объект, вызывающий метод `AttachProfiler` (например, код триггера, созданный разработчиком профилировщика), отвечает за выделение и освобождение памяти для данных, на которые указывает параметр `pvClientData`. Когда среда CLR выполняет вызов `AttachProfiler`, создается копия памяти, на которую указывает `pvClientData`, которая затем передается в целевой процесс. Когда среда CLR в целевом процессе получает собственную копию блока `pvClientData`, она передает этот блок в профилировщик с помощью метода `InitializeForAttach`, а затем освобождает свою копию блока `pvClientData` в целевом процессе.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Интерфейс ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Профилирование](index.md)
