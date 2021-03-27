---
title: Clrver.exe (средство проверки версий среды CLR)
description: Изучите Clrver.exe, средство проверки версий среды CLR. Это средство выводит отчет обо всех установленных на компьютере версиях среды CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 0787cdf09d55a8464db7f5495b5aeed52c22f5d4
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654184"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="64636-104">Clrver.exe (средство проверки версий среды CLR)</span><span class="sxs-lookup"><span data-stu-id="64636-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="64636-105">Программа версий среды CLR (Clrver.exe) выводит отчет обо всех установленных версиях среды CLR на компьютере.</span><span class="sxs-lookup"><span data-stu-id="64636-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="64636-106">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64636-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="64636-107">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="64636-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="64636-108">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="64636-108">At the command prompt, enter the following command:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64636-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64636-109">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="64636-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="64636-110">Options</span></span>  
  
|<span data-ttu-id="64636-111">Параметр</span><span class="sxs-lookup"><span data-stu-id="64636-111">Option</span></span>|<span data-ttu-id="64636-112">Описание</span><span class="sxs-lookup"><span data-stu-id="64636-112">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="64636-113">Отображает все процессы на компьютере, которые используют среду CLR.</span><span class="sxs-lookup"><span data-stu-id="64636-113">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="64636-114">*pid*</span><span class="sxs-lookup"><span data-stu-id="64636-114">*pid*</span></span>|<span data-ttu-id="64636-115">Отображает версии среды CLR, используемой процессом с указанным идентификатором процесса (PID).</span><span class="sxs-lookup"><span data-stu-id="64636-115">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="64636-116">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="64636-116">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64636-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="64636-117">Remarks</span></span>  

 <span data-ttu-id="64636-118">Если программа Clrver.exe вызывается без параметров, отображаются все установленные версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="64636-118">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="64636-119">Если указан PID для другого пользователя, для получения сведений о версии необходимо иметь права администратора.</span><span class="sxs-lookup"><span data-stu-id="64636-119">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64636-120">В Windows Vista и более поздних версиях права доступа пользователя определяются контролем учетных записей.</span><span class="sxs-lookup"><span data-stu-id="64636-120">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="64636-121">Члену встроенной группы "Администраторы" присваивается два маркера доступа на время выполнения: маркер доступа обычного пользователя и маркер доступа администратора.</span><span class="sxs-lookup"><span data-stu-id="64636-121">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="64636-122">По умолчанию назначена роль обычного пользователя.</span><span class="sxs-lookup"><span data-stu-id="64636-122">By default, you are in the standard user role.</span></span> <span data-ttu-id="64636-123">Чтобы выполнить код, требующий прав администратора, необходимо сначала повысить права доступа со стандартного пользователя до администратора.</span><span class="sxs-lookup"><span data-stu-id="64636-123">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="64636-124">Это можно сделать при запуске командной строки, щелкнув правой кнопкой мыши значок командной строки и указав, что приложение должно выполняться от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="64636-124">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="64636-125">При попытке определить версию среды CLR для процессов SYSTEM, LOCAL SERVICE и NETWORK SERVICE выводится сообщение о том, что PID не существует.</span><span class="sxs-lookup"><span data-stu-id="64636-125">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="64636-126">Примеры</span><span class="sxs-lookup"><span data-stu-id="64636-126">Examples</span></span>  

 <span data-ttu-id="64636-127">Приведенная ниже команда отображает все установленные на компьютере версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="64636-127">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="64636-128">Следующая команда отображает версию среды CLR, используемую процессом 128.</span><span class="sxs-lookup"><span data-stu-id="64636-128">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="64636-129">Следующая команда отображает все управляемые процессы и версию среды CLR, которую они используют.</span><span class="sxs-lookup"><span data-stu-id="64636-129">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="64636-130">См. также</span><span class="sxs-lookup"><span data-stu-id="64636-130">See also</span></span>

- [<span data-ttu-id="64636-131">Инструменты</span><span class="sxs-lookup"><span data-stu-id="64636-131">Tools</span></span>](index.md)
- [<span data-ttu-id="64636-132">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="64636-132">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
