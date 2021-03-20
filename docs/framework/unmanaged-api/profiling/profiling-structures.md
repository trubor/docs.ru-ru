---
description: 'Дополнительные сведения: Профилирование структур'
title: Структуры профилирования
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 176830cac519f22864ba004b176cb575d80e50e2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760240"
---
# <a name="profiling-structures"></a>Структуры профилирования

В этом разделе описаны неуправляемые структуры, которые использует API профилирования.  
  
## <a name="in-this-section"></a>В этом разделе  

 [Структура COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)  
 Обеспечивает среду CLR информацией о ссылке на сборку, которую ей следует учитывать при выполнении обхода замыкания.  
  
 [Структура COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)  
 Представляет один непрерывный блок машинного кода, хранящийся в памяти.  
  
 [Структура COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)  
 Хранит сведения об определенном экземпляре исключительного предложения и связанном с ним кадре.  
  
 [Структура COR_PRF_FUNCTION](cor-prf-function-structure.md)  
 Выдает уникальное представление функции, объединяя ее идентификатор с идентификатором перекомпилированной версии этой функции.  
  
 [Структура COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)  
 Представляет аргументы функции слева направо.  
  
 [Структура COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)  
 Представляет блок аргументов функции, которые сохраняются в памяти последовательно слева направо.  
  
 [Структура COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)  
 Описывает диапазон (т. е., блок) памяти, который занимается сборкой мусора.  

 [Структура COR_PRF_EVENTPIPE_PROVIDER_CONFIG](cor-prf-eventpipe-provider-config-structure.md) Описание полей, необходимых для настройки поставщика Евентпипе.

 [Структура COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) Описывает имя и тип параметра для события Евентпипе.

 [Структура COR_PRF_EVENT_DATA](cor-prf-event-data-structure.md) Описывает данные события для записываемого события Евентпипе.
  
## <a name="related-sections"></a>Связанные разделы  

 COR_DEBUG_IL_TO_NATIVE_MAP  
  
 COR_IL_MAP  
  
 [Общие сведения о профилировании](profiling-overview.md)  
  
 [Профилирующие интерфейсы](profiling-interfaces.md)  
  
 [Глобальные статические функции профилирования](profiling-global-static-functions.md)  
  
 [Перечисления профилирования](profiling-enumerations.md)
