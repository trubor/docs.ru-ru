---
description: Дополнительные сведения о интерфейсе ICorDebug
title: Интерфейс ICorDebug
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: db6c407e3361ebd9c39dd2c3cf7e5b53a69e0559
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494835"
---
# <a name="icordebug-interface"></a>Интерфейс ICorDebug

Предоставляет методы, позволяющие разработчикам отлаживать приложения в среде среды CLR.  
  
> [!NOTE]
> Отладка в смешанном режиме (управляемый и машинный код) не поддерживается на платформах, отличных от x86 (например, IA64 и AMD64).  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод CanLaunchOrAttach](icordebug-canlaunchorattach-method.md)|Определяет, возможен ли запуск нового процесса или присоединение к данному процессу в контексте текущей конфигурации компьютера и среды выполнения.|  
|[Метод CreateProcess](icordebug-createprocess-method.md)|Запускает процесс и его основной поток под управлением отладчика.|  
|[Метод DebugActiveProcess](icordebug-debugactiveprocess-method.md)|Присоединяет отладчик к существующему процессу.|  
|[Метод EnumerateProcesses](icordebug-enumerateprocesses-method.md)|Возвращает перечислитель для отлаживаемых процессов.|  
|[Метод GetProcess](icordebug-getprocess-method.md)|Возвращает объект "ICorDebugProcess" с заданным ИДЕНТИФИКАТОРом процесса.|  
|[Метод Initialize](icordebug-initialize-method.md)|Выполняет инициализацию объекта `ICorDebug`.|  
|[Метод SetManagedHandler](icordebug-setmanagedhandler-method.md)|Указывает объект обработчика событий для управляемых событий.|  
|[Метод SetUnmanagedHandler](icordebug-setunmanagedhandler-method.md)|Указывает объект обработчика событий для неуправляемых событий.|  
|[Метод Terminate](icordebug-terminate-method.md)|Завершает `ICorDebug` объект.|  
  
## <a name="remarks"></a>Комментарии  

 `ICorDebug` представляет цикл обработки событий для процесса отладчика. Перед освобождением этого интерфейса отладчик должен ожидать обратного вызова [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) для всех отлаживаемых процессов.  
  
 `ICorDebug`Объект является начальным объектом для управления всеми дальнейшими управляемыми отладками. В платформа .NET Framework версиях 1,0 и 1,1 этот объект был `CoClass` объектом, созданным из com. В платформа .NET Framework версии 2,0 этот объект больше не является `CoClass` объектом. Она должна быть создана функцией [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) , которая поддерживает больше версий. Эта новая функция создания позволяет клиентам получить определенную реализацию `ICorDebug` , которая также эмулирует определенную версию API отладки.  
  
> [!NOTE]
> Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейсы отладки](debugging-interfaces.md)
