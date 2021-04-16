---
title: События среды выполнения системы типов
description: См. события среды выполнения .NET, собирающие диагностическую информацию, относящуюся к системе типов .NET, например TypeLoadStart и TypeLoadStop.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594038"
---
# <a name="net-runtime-type-events"></a>События типов среды выполнения .NET

Эти события собирают сведения, связанные с загрузкой типов. Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).

## <a name="typeloadstart-event"></a>Событие TypeLoadStart

|Ключевое слово для вызова события|Событие|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Информационный (4)|  

|Событие|Идентификатор события|Описание|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|73|Начата загрузка типа.|

|Имя поля|Тип данных|Описание|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|Идентификатор операции загрузки типа.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|  

## <a name="typeloadstop-event"></a>Событие TypeLoadStop

|Ключевое слово для вызова события|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Информационный (4)|  

|Событие|Идентификатор события|Описание|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|74|Загрузка типа завершена.|

|Имя поля|Тип данных|Описание|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|Идентификатор для операции загрузки типа (совпадает с TypeLoadStartID соответствующего события TypeLoadStart).|
|`LoadLevel`|`win:UInt16`|Уровень загрузки типа.|
|`TypeID`|`win:UInt64`|Указатель на дескриптор типа.|
|`TypeName`|`win:UnicodeString`|Имя типа данных.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|  
