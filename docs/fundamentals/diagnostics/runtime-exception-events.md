---
title: События исключения среды выполнения
description: Сведения о событиях среды выполнения .NET, собирающих диагностическую информацию, относящуюся к исключениям и обработке исключений.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594104"
---
# <a name="net-runtime-exception-events"></a>События исключения среды выполнения .NET

Эти события среды выполнения собирают сведения о возникших исключениях. Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).

## <a name="exceptionthrown_v1-event"></a>Событие ExceptionThrown_V1

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Ошибка (1)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|Возникло управляемое исключение.|

|Имя поля|Тип данных|Описание|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|Тип исключения, например `System.NullReferenceException`.|
|`ExceptionMessage`|`win:UnicodeString`|Фактическое сообщение об исключении.|
|`EIPCodeThrow`|`win:Pointer`|Указатель на инструкцию, в которой возникло исключение.|
|`ExceptionHR`|`win:UInt32`|Исключение [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException.<br /><br /> `0x02`: IsNestedException.<br /><br /> `0x04`: IsRethrownException.<br /><br /> `0x08`: IsCorruptedStateException (указывает, что процесс находится в поврежденном состоянии, см. раздел [Обработка исключений поврежденного состояния](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> `0x10`: IsCLSCompliant (исключение, производное от <xref:System.Exception>, является CLS-совместимым; в противном случае такое исключение не является CLS-совместимым).|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|

## <a name="exceptioncatchstart-event"></a>Событие ExceptionCatchStart

Это событие возникает при запуске обработчика перехвата управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|Управляемое исключение обрабатывается средой выполнения.|

|Имя поля|Тип данных|Описание|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Указатель на инструкцию, в которой возникло исключение.|
|`MethodID`|`win:Pointer`|Указатель на дескриптор метода в методе, где возникло исключение.|
|`MethodName`|`win:UnicodeString`|Имя метода, где возникло исключение.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|

## <a name="exceptioncatchstop-event"></a>Событие ExceptionCatchStop

Это событие возникает при завершении работы обработчика перехвата управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|Работа обработчика перехвата управляемых исключений завершена.|

## <a name="exceptionfinallystart-event"></a>Событие ExceptionFinallyStart

Это событие возникает при окончательном запуске обработчика перехвата управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|Управляемое исключение обрабатывается средой выполнения.|

|Имя поля|Тип данных|Описание|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Указатель на инструкцию, в которой возникло исключение.|
|`MethodID`|`win:Pointer`|Указатель на дескриптор метода в методе, где возникло исключение.|
|`MethodName`|`win:UnicodeString`|Имя метода, где возникло исключение.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор экземпляра CLR или CoreCLR.|

## <a name="exceptionfinallystop-event"></a>Событие ExceptionFinallyStop

Это событие возникает при завершении работы обработчика перехвата управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|Обработчик перехвата управляемых исключений окончательно остановлен.|

## <a name="exceptionfilterstart-event"></a>Событие ExceptionFilterStart

Это событие возникает при начале фильтрации управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|Начинается фильтрация управляемого исключения.|

|Имя поля|Тип данных|Описание|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Указатель на инструкцию, в которой возникло исключение.|
|`MethodID`|`win:Pointer`|Указатель на дескриптор метода в методе, где возникло исключение.|
|`MethodName`|`win:UnicodeString`|Имя метода, где возникло исключение.|
|`ClrInstanceID`|`win:UInt16`|Уникальный идентификатор для экземпляра CoreCLR.|

## <a name="exceptionfilterstop-event"></a>Событие ExceptionFilterStop

Это событие возникает при окончании фильтрации управляемых исключений.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|

 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|Заканчивается фильтрация управляемого исключения.|

## <a name="exceptionthrownstop-event"></a>Событие ExceptionThrownStop

Это событие вызывается, когда среда выполнения завершила обработку созданного управляемого исключение.

|Ключевое слово для вызова события|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Информационный (4)|
  
 В таблице ниже представлены сведения о событии.

|Событие|Идентификатор события|Условие вызова|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|Заканчивается фильтрация управляемого исключения.|
