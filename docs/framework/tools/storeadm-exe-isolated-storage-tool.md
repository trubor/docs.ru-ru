---
title: Storeadm.exe (средство изолированного хранилища)
description: Ознакомьтесь с Storeadm.exe, средством изолированного хранилища. С его помощью можно получить список или удалить все существующие хранилища для текущего пользователя.
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 89eb2b35dc640f21f3d6d6ca7f477841f1a020c7
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494042"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (средство изолированного хранилища)

Программа изолированного хранилища выводит список или удаляет все существующие хранилища для текущего пользователя.  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|------------|-----------------|  
|**/h**[**elp**]|Отображает синтаксис команд и параметров программы.|  
|**/list**|Отображает все существующие хранилища для текущего пользователя. В их число включаются хранилища для всех приложений или сборок, выполненных данным пользователем.|  
|**/machine**|Выбирает хранилище компьютера. Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к хранилищу компьютера.<br /><br /> Новые возможности в .NET Framework 2.0|  
|**/quiet**|Определяет тихий режим, отключает вывод всех сообщений, кроме сообщений об ошибках.|  
|**/remove**|Полностью удаляет все существующие хранилища для текущего пользователя.|  
|**/roaming**|Задает перемещаемое хранилище. Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к перемещаемому хранилищу.|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
  
## <a name="remarks"></a>Примечания  

 При запуске программы Storeadm.exe из командной строки без указания параметров будут отображены ее синтаксис и параметры.  
  
 Обычно используется лишь один из параметров **/list** и **/remove**, однако при использовании нескольких параметров они будут обрабатываться в порядке их указания в командной строке.  
  
 Приложение может выбрать для сохранения одно из двух хранилищ пользователя или хранилище компьютера.  
  
- Локальное хранилище располагается там, где данные точно не будут перемещаться, даже если их перемещение для пользователя включено.  
  
- Перемещаемое хранилище располагается там, где возможно перемещение данных, однако нужно обязательно включить его для пользователя в средствах администрирования Windows.  
  
- Хранилище компьютера является общим для всех пользователей данного компьютера и располагается в его общем каталоге.
  
Управление программой Storeadm.exe не зависит от того, включен ли режим перемещения для пользователя. При запуске программы без параметров все действия применяются к локальному хранилищу. При запуске программы с параметром **/roaming** все действия будут применяться к перемещаемому хранилищу. При запуске программы с параметром **/machine** все действия применяются к хранилищу компьютера.  
  
## <a name="see-also"></a>См. также

- [Инструменты](index.md)
- [Изолированное хранилище](../../standard/io/isolated-storage.md)
- [Оболочки командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell)
