---
title: Winmdexp.exe (средство экспорта метаданных среды выполнения Windows)
description: Узнайте о Winmdexp.exe, средстве экспорта метаданных среды выполнения Windows. Это средство преобразует модуль .NET в файл, который содержит метаданные среды выполнения Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: b9a30076fdd67a90dc3e605a8014ead88141f43b
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477537"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (средство экспорта метаданных среды выполнения Windows)

Программа экспорта метаданных среды выполнения Windows (Winmdexp.exe) преобразует модуль .NET Framework в файл, содержащий метаданные среды выполнения Windows. Несмотря на то что сборки .NET Framework и файлы метаданных среды выполнения Windows используют один и тот же физический формат, существуют различия в содержимом таблиц метаданных, то есть сборки .NET Framework невозможно без преобразования использовать как компоненты среды выполнения Windows. Процесс преобразования модуля .NET Framework в компонент среды выполнения Windows называется *экспортированием*. В .NET Framework 4.5 и .NET Framework 4.5.1 конечный файл метаданных Windows (WINMD) содержит и метаданные, и реализацию.  
  
 При использовании шаблона **Компонент среды выполнения Windows** из **Microsoft Store** для C# и Visual Basic в Visual Studio 2013 или Visual Studio 2012 компилятор создает WINMDOBJ-файл, а на последующих этапах сборки вызывается программа Winmdexp.exe, чтобы экспортировать WINMDOBJ-файл в WINMD-файл. Это рекомендуемый способ создания компонента среды выполнения Windows. Если над процессом построения требуется больший контроль по сравнению со средой Visual Studio, программу Winmdexp.exe следует вызывать напрямую.  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Параметры  
  
|Аргумент или параметр|Описание|  
|------------------------|-----------------|  
|`winmdmodule`|Задает экспортируемый модуль (WINMDOBJ). Допускается только один модуль. Чтобы создать этот модуль, следует использовать параметр компилятора `/target` с целевым объектом `winmdobj`. См. раздел [-target:winmdobj (параметры компилятора C#)](../../csharp/language-reference/compiler-options/output.md#targettype) или [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Задает выходной файл документации XML, который создаст программа Winmdexp.exe. В .NET Framework 4.5 выходной файл совпадает со входным файлом XML документации.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Задает имя файла документации XML, который компилятор создает с использованием `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Задает имя файла базы данных программы (PDB), содержащего символы для `winmdmodule`.|  
|`/nowarn:` `warning`|Отключает указанный номер предупреждения. В качестве *предупреждения* следует указать только числовую часть кода ошибки без предшествующих нулей.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Задает имя выходного файла метаданных Windows (WINMD).|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Задает имя выходного файла базы данных программы (PDB), в котором будут указаны символы для экспортированного файла метаданных Windows (WINMD).|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Задает файл метаданных (WINMD или сборку), на который необходимо ссылаться во время экспорта. Если используются ссылочные сборки в \Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5 (\Program Files\\... на 32-разрядных компьютерах), следует включить ссылки как на библиотеку System.Runtime.dll, так и на mscorlib.dll.|  
|`/utf8output`|Указывает, что выходные сообщения должны иметь кодировку UTF-8.|  
|`/warnaserror+`|Указывает, что все предупреждения должны рассматриваться как ошибки.|  
|**@** `responsefile`|Задает файл ответа (RSP), содержащий параметры (и при необходимости — `winmdmodule`). Каждая строка в файле `responsefile` должна содержать один аргумент или параметр.|  
  
## <a name="remarks"></a>Примечания  

 Программа Winmdexp.exe не предназначена для преобразования произвольной сборки .NET Framework в WINMD-файл. Для ее работы требуется модуль, который скомпилирован с параметром `/target:winmdobj`, и использование дополнительных ограничений. Наиболее важным ограничением является то, что все типы, которые отображаются в рабочей области API сборки, должны быть типами среды выполнения Windows. Дополнительные сведения см. в разделе "Объявление типов в компонентах среды выполнения Windows" статьи [Создание компонентов среды выполнения Windows на языках C# и Visual Basic](/previous-versions/br230301(v=vs.110)).
  
 Платформа .NET Framework упрощает программирование в среде выполнения Windows и делает его более естественным при создании приложений Магазина Windows 8.x или компонентов среды выполнения Windows на C# или Visual Basic. Это рассматривается в статье [Поддержка платформы .NET Framework для приложений Магазина Windows и среды выполнения Windows](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md). Во время разработки некоторые часто используемые типы среды выполнения Windows сопоставляются с типами .NET Framework. Программа Winmdexp.exe позволяет упростить такой процесс и создает рабочую область API, в которой используются соответствующие типы среды выполнения Windows. Например, типы, полученные из интерфейса <xref:System.Collections.Generic.IList%601>, сопоставляются с типами, полученными из интерфейса <xref:Windows.Foundation.Collections.IVector%601> среды выполнения Windows.  
  
## <a name="see-also"></a>См. также

- [Поддержка платформы .NET Framework для приложений магазина Windows и среды выполнения Windows](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Создание компонентов среды выполнения Windows в C# и Visual Basic](/previous-versions/br230301(v=vs.110))
- [Сообщения об ошибках Winmdexp.exe](winmdexp-exe-error-messages.md)
- [Средства построения, развертывания и конфигурирования (платформа .NET Framework)](/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
