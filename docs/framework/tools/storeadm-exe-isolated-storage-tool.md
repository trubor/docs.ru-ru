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
ms.openlocfilehash: e6c2fc15ba2b6fef27bb57344628638a99103916
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258742"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="f2b8d-104">Storeadm.exe (средство изолированного хранилища)</span><span class="sxs-lookup"><span data-stu-id="f2b8d-104">Storeadm.exe (Isolated Storage Tool)</span></span>

<span data-ttu-id="f2b8d-105">Программа изолированного хранилища выводит список или удаляет все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="f2b8d-106">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f2b8d-107">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="f2b8d-107">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
 <span data-ttu-id="f2b8d-108">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b8d-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2b8d-109">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b8d-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="f2b8d-110">Parameters</span></span>  
  
|<span data-ttu-id="f2b8d-111">Параметр</span><span class="sxs-lookup"><span data-stu-id="f2b8d-111">Option</span></span>|<span data-ttu-id="f2b8d-112">Описание</span><span class="sxs-lookup"><span data-stu-id="f2b8d-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f2b8d-113">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="f2b8d-113">**/h**[**elp**]</span></span>|<span data-ttu-id="f2b8d-114">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-114">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f2b8d-115">**/list**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-115">**/list**</span></span>|<span data-ttu-id="f2b8d-116">Отображает все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-116">Displays all existing stores for the current user.</span></span> <span data-ttu-id="f2b8d-117">В их число включаются хранилища для всех приложений или сборок, выполненных данным пользователем.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-117">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="f2b8d-118">**/machine**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-118">**/machine**</span></span>|<span data-ttu-id="f2b8d-119">Выбирает хранилище компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-119">Selects the machine store.</span></span> <span data-ttu-id="f2b8d-120">Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к хранилищу компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-120">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="f2b8d-121">Новые возможности в .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="f2b8d-121">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="f2b8d-122">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-122">**/quiet**</span></span>|<span data-ttu-id="f2b8d-123">Определяет тихий режим, отключает вывод всех сообщений, кроме сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-123">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="f2b8d-124">**/remove**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-124">**/remove**</span></span>|<span data-ttu-id="f2b8d-125">Полностью удаляет все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-125">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="f2b8d-126">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-126">**/roaming**</span></span>|<span data-ttu-id="f2b8d-127">Задает перемещаемое хранилище.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-127">Selects the roaming store.</span></span> <span data-ttu-id="f2b8d-128">Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к перемещаемому хранилищу.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-128">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="f2b8d-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="f2b8d-129">**/?**</span></span>|<span data-ttu-id="f2b8d-130">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-130">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2b8d-131">Примечания</span><span class="sxs-lookup"><span data-stu-id="f2b8d-131">Remarks</span></span>  

 <span data-ttu-id="f2b8d-132">При запуске программы Storeadm.exe из командной строки без указания параметров будут отображены ее синтаксис и параметры.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-132">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="f2b8d-133">Обычно используется лишь один из параметров **/list** и **/remove**, однако при использовании нескольких параметров они будут обрабатываться в порядке их указания в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-133">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="f2b8d-134">Приложение может выбрать для сохранения одно из двух хранилищ пользователя или хранилище компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-134">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="f2b8d-135">Локальное хранилище располагается в том месте, которое гарантированно не является перемещаемым (в Windows 2000 или более поздних версиях), даже если для пользователя включен режим перемещения данных.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-135">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="f2b8d-136">Перемещаемое хранилище располагается в месте, которое можно переместить, но только если для пользователя включен режим перемещения с помощью средств администрирования Windows NT.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-136">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="f2b8d-137">Хранилище компьютера является общим для всех пользователей данного компьютера и располагается в его общем каталоге.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-137">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f2b8d-138">Поддержка хранилища компьютера является новой возможностью .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-138">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="f2b8d-139">Управление программой Storeadm.exe не зависит от того, включен ли режим перемещения для пользователя.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-139">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="f2b8d-140">При запуске программы без параметров все действия применяются к локальному хранилищу.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-140">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="f2b8d-141">При запуске программы с параметром **/roaming** все действия будут применяться к перемещаемому хранилищу.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-141">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="f2b8d-142">При запуске программы с параметром **/machine** все действия применяются к хранилищу компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2b8d-142">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b8d-143">См. также</span><span class="sxs-lookup"><span data-stu-id="f2b8d-143">See also</span></span>

- [<span data-ttu-id="f2b8d-144">Инструменты</span><span class="sxs-lookup"><span data-stu-id="f2b8d-144">Tools</span></span>](index.md)
- [<span data-ttu-id="f2b8d-145">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="f2b8d-145">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="f2b8d-146">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="f2b8d-146">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
