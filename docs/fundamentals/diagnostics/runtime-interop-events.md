---
title: События взаимодействия среды выполнения
description: Сведения о событиях среды выполнения .NET, собирающих диагностическую информацию, относящуюся к взаимодействию.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Interop events (CoreCLR)
- ETW, EventPipe, LTTng interop events (CoreCLR)
ms.openlocfilehash: 5635fb55b3a6ffa3f5611da80cdb2909e226e2ea
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594047"
---
# <a name="net-runtime-interop-events"></a>События взаимодействия среды выполнения .NET

Эти события среды выполнения собирают сведения о создании заглушки CIL. Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).

## <a name="ilstubgenerated-event"></a>Событие ILStubGenerated

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`InteropKeyword` (0x2000)|Информационный (4)|
  
|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ILStubGenerated`|88|Создается заглушка IL.|

|Имя поля|Тип данных|Описание|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt16`|Идентификатор модуля.|
|`StubMethodID`|`win:UInt64`|Идентификатор метода-заглушки.|
|`StubFlags`|`win:UInt32`|Флаги для заглушки:<br /><br /> `0x1` — обратное взаимодействие.<br /><br /> `0x2` — взаимодействие COM.<br /><br /> `0x4` — заглушка, созданная программой NGen.exe.<br /><br /> `0x8` — делегат.<br /><br /> `0x10` — аргумент переменной.<br /><br /> `0x20` — неуправляемый вызываемый объект.<br /><br /> `0x40` — маршалирование структуры.|
|`ManagedInteropMethodToken`|`win:UInt32`|Токен управляемого метода взаимодействия.|
|`ManagedInteropMethodNameSpace`|`win:UnicodeString`|Пространство имен и включающий тип управляемого метода взаимодействия.|
|`ManagedInteropMethodName`|`win:UnicodeString`|Имя управляемого метода взаимодействия.|
|`ManagedInteropMethodSignature`|`win:UnicodeString`|Сигнатура управляемого метода взаимодействия.|
|`NativeMethodSignature`|`win:UnicodeString`|Сигнатура неуправляемого метода.|
|`StubMethodSignature`|`win:UnicodeString`|Сигнатура метода-заглушки.|
|`StubMethodILCode`|`win:UnicodeString`|Код для метода-заглушки.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|
