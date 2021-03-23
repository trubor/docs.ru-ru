---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo9'
title: Интерфейс ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 44e3d694b426f87ee4e4bc12181f46322b0d246f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805679"
---
# <a name="icorprofilerinfo9-interface"></a>Интерфейс ICorProfilerInfo9

Подкласс [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , предоставляющий методы для запроса сведений о функциях с несколькими версиями машинного кода.  

## <a name="methods"></a>Методы  

| Метод|Описание|  
| ------------|-----------------|  
|[Метод GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют. |
|[Метод GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода. |
|[Метод GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код. |

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]  

## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
