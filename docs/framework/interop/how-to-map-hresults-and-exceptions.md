---
title: Практическое руководство. Сопоставление значений HRESULT и исключений
description: Узнайте, как сопоставлять значения HRESULT, возвращаемые методами COM, с исключениями, которые создаются методами .NET. Среда выполнения поддерживает переход между COM и .NET.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: 13798de1547428d54c10f83c41a5a402e2b3fb53
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872409"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Практическое руководство. Сопоставление значений HRESULT и исключений

Методы COM сообщают об ошибках, возвращая значения HRESULT. Методы .NET в этом случае вызывают исключения. Среда выполнения обеспечивает сопоставление этих двух элементов. Каждый класс платформы .NET Framework сопоставляется со значением HRESULT.

 Соответствующие значения HRESULT задаются определяемыми пользователем классами исключений. Эти классы исключений могут динамически изменять значение HRESULT, возвращаемое при возникновении исключения, устанавливая поле `HResult` соответствующего объекта исключения. Дополнительные сведения об исключении предоставляются клиенту посредством интерфейса `IErrorInfo`, который реализуется для объекта .NET в неуправляемом процессе.

 При создании класса, который расширяет `System.Exception`, необходимо устанавливать значение поля HRESULT во время построения. В противном случае значение HRESULT будет присваиваться базовым классом. Чтобы сопоставить новые классы исключений с существующим значением HRESULT, укажите значение в конструкторе исключения.

 Обратите внимание, что среда выполнения в некоторых случаях будет игнорировать значение `HRESULT`, если в потоке присутствует `IErrorInfo`.  Это возможно в тех случаях, когда `HRESULT` и `IErrorInfo` представляют разные ошибки.

### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Создание нового класса исключения и его сопоставление со значением HRESULT

1. В следующем коде создается новый класс исключения `NoAccessException`, который сопоставляется со значением HRESULT `E_ACCESSDENIED`.

    ```cpp
    Class NoAccessException : public ApplicationException
    {
        NoAccessException () {
        HResult = E_ACCESSDENIED;
    }
    }
    CMyClass::MethodThatThrows
    {
    throw new NoAccessException();
    }
    ```

 На любом языке программирования могут встречаться программы, в которых одновременно используется управляемый и неуправляемый код. Например, в настраиваемом маршалере в следующем коде используется метод `Marshal.ThrowExceptionForHR(int HResult)` , который вызывает исключение с заданным значением HRESULT. Этот метод выполняет поиск значения HRESULT и создает исключение соответствующего типа. Например, в следующем коде для заданного значения HRESULT создается `ArgumentException`.

```cpp
CMyClass::MethodThatThrows
{
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);
}
```

 В следующей таблице приводится общий перечень сопоставлений значений HRESULT с соответствующими классами исключений в .NET. Значения HRESULT без явных сопоставлений сопоставляются с `COMException`. Актуальные сведения о сопоставлении представлены в [репозитории среды выполнения/dotnet](https://github.com/dotnet/runtime/blob/main/src/coreclr/vm/rexcep.h).

|HRESULT|Исключение .NET|
|-------------|--------------------|
|`COR_E_APPLICATION`|`ApplicationException`|
|`COR_E_ARGUMENT` либо `E_INVALIDARG`|`ArgumentException`|
|`COR_E_ARGUMENTOUTOFRANGE`|`ArgumentOutOfRangeException`|
|`COR_E_ARITHMETIC or ERROR_ARITHMETIC_OVERFLOW`|`ArithmeticException`|
|`COR_E_ARRAYTYPEMISMATCH`|`ArrayTypeMismatchException`|
|`COR_E_BADIMAGEFORMAT or ERROR_BAD_FORMAT`|`BadImageFormatException`|
|`COR_E_DIRECTORYNOTFOUND or ERROR_PATH_NOT_FOUND`|`DirectoryNotFoundException`|
|`COR_E_DIVIDEBYZERO`|`DivideByZeroException`|
|`COR_E_DUPLICATEWAITOBJECT`|`DuplicateWaitObjectException`|
|`COR_E_ENDOFSTREAM`|`EndOfStreamException`|
|`COR_E_ENTRYPOINTNOTFOUND`|`EntryPointNotFoundException`|
|`COR_E_EXCEPTION`|`Exception`|
|`COR_E_EXECUTIONENGINE`|`ExecutionEngineException`|
|`COR_E_FIELDACCESS`|`FieldAccessException`|
|`COR_E_FILENOTFOUND or ERROR_FILE_NOT_FOUND`|`FileNotFoundException`|
|`COR_E_FORMAT`|`FormatException`|
|`COR_E_INDEXOUTOFRANGE`|`IndexOutOfRangeException`|
|`COR_E_INVALIDCAST or E_NOINTERFACE`|`InvalidCastException`|
|`COR_E_INVALIDFILTERCRITERIA`|`InvalidFilterCriteriaException`|
|`COR_E_INVALIDOPERATION`|`InvalidOperationException`|
|`COR_E_IO`|`IOException`|
|`COR_E_MEMBERACCESS`|`AccessException`|
|`COR_E_METHODACCESS`|`MethodAccessException`|
|`COR_E_MISSINGFIELD`|`MissingFieldException`|
|`COR_E_MISSINGMANIFESTRESOURCE`|`MissingManifestResourceException`|
|`COR_E_MISSINGMEMBER`|`MissingMemberException`|
|`COR_E_MISSINGMETHOD`|`MissingMethodException`|
|`COR_E_NOTFINITENUMBER`|`NotFiniteNumberException`|
|`E_NOTIMPL`|`NotImplementedException`|
|`COR_E_NOTSUPPORTED`|`NotSupportedException`|
|`COR_E_NULLREFERENCE orE_POINTER`|`NullReferenceException`|
|`COR_E_OUTOFMEMORY or`<br /><br /> `E_OUTOFMEMORY`|`OutOfMemoryException`|
|`COR_E_OVERFLOW`|`OverflowException`|
|`COR_E_PATHTOOLONG or ERROR_FILENAME_EXCED_RANGE`|`PathTooLongException`|
|`COR_E_RANK`|`RankException`|
|`COR_E_REFLECTIONTYPELOAD`|`ReflectionTypeLoadException`|
|`COR_E_SECURITY`|`SecurityException`|
|`COR_E_SERIALIZATION`|`SerializationException`|
|`COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW`|`StackOverflowException`|
|`COR_E_SYNCHRONIZATIONLOCK`|`SynchronizationLockException`|
|`COR_E_SYSTEM`|`SystemException`|
|`COR_E_TARGET`|`TargetException`|
|`COR_E_TARGETINVOCATION`|`TargetInvocationException`|
|`COR_E_TARGETPARAMCOUNT`|`TargetParameterCountException`|
|`COR_E_THREADINTERRUPTED`|`ThreadInterruptedException`|
|`COR_E_THREADSTATE`|`ThreadStateException`|
|`COR_E_TYPELOAD`|`TypeLoadException`|
|`COR_E_TYPEINITIALIZATION`|`TypeInitializationException`|
|`COR_E_VERIFICATION`|`VerificationException`|

 Чтобы получить дополнительные сведения об ошибке, управляемый клиент должен проверить поля созданного объекта исключения. Чтобы объект исключения содержал полезные сведения об ошибке, COM-объект должен реализовывать интерфейс `IErrorInfo`. Среда выполнения использует сведения, предоставляемые интерфейсом `IErrorInfo`, для инициализации объекта исключения.

 Если COM-объект не поддерживает интерфейс `IErrorInfo`, среда выполнения инициализирует объект исключения с использованием значений по умолчанию. В следующей таблице перечислены все поля, связанные с объектом исключения, и указан источник сведений по умолчанию для случаев, когда COM-объект поддерживает `IErrorInfo`.

 Обратите внимание, что среда выполнения в некоторых случаях будет игнорировать значение `HRESULT`, если в потоке присутствует `IErrorInfo`.  Это возможно в тех случаях, когда `HRESULT` и `IErrorInfo` представляют разные ошибки.

|Поле Exception|Источник сведений из модели COM|
|---------------------|------------------------------------|
|`ErrorCode`|Значение HRESULT, возвращенное из вызова.|
|`HelpLink`|Если `IErrorInfo->HelpContext` не равно нулю, строка формируется путем сцепления строк `IErrorInfo->GetHelpFile`, "#" и `IErrorInfo->GetHelpContext`. В противном случае возвращается строка из `IErrorInfo->GetHelpFile`.|
|`InnerException`|Всегда ссылка NULL (`Nothing` в Visual Basic).|
|`Message`|Строка, возвращаемая `IErrorInfo->GetDescription`.|
|`Source`|Строка, возвращаемая `IErrorInfo->GetSource`.|
|`StackTrace`|Трассировка стека.|
|`TargetSite`|Имя метода, который вернул значение HRESULT со сбоем.|

 Поля исключения `Message`, `Source` и `StackTrace` недоступны для `StackOverflowException`.

## <a name="see-also"></a>См. также

- [Расширенное COM-взаимодействие](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Исключения](../../standard/exceptions/index.md)
