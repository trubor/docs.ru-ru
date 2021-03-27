---
title: CorFlags.exe (средство преобразования CorFlags)
description: Ознакомьтесь с CorFlags.exe, средством преобразования CorFlags. Это средство позволяет настраивать раздел CorFlags заголовка переносимого исполняемого образа.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 2b801ba28e0513c899123daa98fd649cbc3d9c28
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654171"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (средство преобразования CorFlags)

Средство преобразования CorFlags позволяет настраивать раздел CorFlags в заголовке переносимого исполняемого образа.  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Обязательный параметр|Описание|  
|------------------------|-----------------|  
|`assembly`|Имя сборки, для которой требуется настроить раздел CorFlags.|  
  
|Параметр|Описание|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|Устанавливает флаг 32BITREQUIRED.|  
|`-32BIT[REQ]-`|Снимает флаг 32BITREQUIRED.|  
|`-32BITPREF+`|Устанавливает флаг 32BITPREFERRED. Приложение выполняется как 32-разрядный процесс даже на 64-разрядных платформах. Устанавливайте этот флаг только в EXE-файлах. Если флаг установлен для библиотеки DLL, она не загружается в 64-разрядных процессах и создается исключение <xref:System.BadImageFormatException>. Файл EXE с этим флагом можно загрузить в 64-разрядный процесс.<br /><br /> Новые возможности .NET Framework 4.5.|  
|`-32BITPREF-`|Снимает флаг 32BITPREFERRED.<br /><br /> Новые возможности .NET Framework 4.5.|  
|`-?`|Отображает синтаксис команд и параметров программы.|  
|`-Force`|Выполняет принудительное обновление, даже если сборка имеет строгое имя. **Внимание!**  При обновлении сборки со строгим именем перед выполнением ее кода необходимо снова подписать сборку.|  
|`-help`|Отображает синтаксис команд и параметров программы.|  
|`-ILONLY+`|Устанавливает флаг ILONLY.|  
|`-ILONLY-`|Снимает флаг ILONLY.|  
|`-nologo`|Отключает отображение эмблемы Майкрософт при запуске.|  
|`-RevertCLRHeader`|Задает версии заголовка CLR значение 2.0.|  
|`-UpgradeCLRHeader`|Обновляет версию заголовка CLR до версии 2.5. **Примечание.**  Для оптимального выполнения сборок они должны иметь версию заголовка CLR 2.5.|  
  
## <a name="remarks"></a>Примечания  

 Если другие параметры не заданы, средство преобразования CorFlags отображает флаги заданной сборки.  
  
## <a name="see-also"></a>См. также

- [Инструменты](index.md)
- [64-разрядные приложения](../64-bit-apps.md)
- [Оболочки командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell)
