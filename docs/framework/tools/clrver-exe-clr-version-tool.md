---
title: Clrver.exe (средство проверки версий среды CLR)
description: Изучите Clrver.exe, средство проверки версий среды CLR. Это средство выводит отчет обо всех установленных на компьютере версиях среды CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 3a7a585d990051553aa8fdc0e99b2dc206273cf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247230"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="b8f4a-104">Clrver.exe (средство проверки версий среды CLR)</span><span class="sxs-lookup"><span data-stu-id="b8f4a-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="b8f4a-105">Программа версий среды CLR (Clrver.exe) выводит отчет обо всех установленных версиях среды CLR на компьютере.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="b8f4a-106">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b8f4a-107">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b8f4a-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b8f4a-108">Дополнительные сведения см. в разделе [Командные строки](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b8f4a-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b8f4a-109">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f4a-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8f4a-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="b8f4a-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="b8f4a-111">Options</span></span>  
  
|<span data-ttu-id="b8f4a-112">Параметр</span><span class="sxs-lookup"><span data-stu-id="b8f4a-112">Option</span></span>|<span data-ttu-id="b8f4a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b8f4a-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="b8f4a-114">Отображает все процессы на компьютере, которые используют среду CLR.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="b8f4a-115">*pid*</span><span class="sxs-lookup"><span data-stu-id="b8f4a-115">*pid*</span></span>|<span data-ttu-id="b8f4a-116">Отображает версии среды CLR, используемой процессом с указанным идентификатором процесса (PID).</span><span class="sxs-lookup"><span data-stu-id="b8f4a-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="b8f4a-117">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f4a-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="b8f4a-118">Remarks</span></span>  

 <span data-ttu-id="b8f4a-119">Если программа Clrver.exe вызывается без параметров, отображаются все установленные версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="b8f4a-120">Если указан PID для другого пользователя, для получения сведений о версии необходимо иметь права администратора.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8f4a-121">В Windows Vista и более поздних версиях права доступа пользователя определяются контролем учетных записей.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="b8f4a-122">Члену встроенной группы "Администраторы" присваивается два маркера доступа на время выполнения: маркер доступа обычного пользователя и маркер доступа администратора.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="b8f4a-123">По умолчанию назначена роль обычного пользователя.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="b8f4a-124">Чтобы выполнить код, требующий прав администратора, необходимо сначала повысить права доступа со стандартного пользователя до администратора.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="b8f4a-125">Это можно сделать при запуске командной строки, щелкнув правой кнопкой мыши значок командной строки и указав, что приложение должно выполняться от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="b8f4a-126">При попытке определить версию среды CLR для процессов SYSTEM, LOCAL SERVICE и NETWORK SERVICE выводится сообщение о том, что PID не существует.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b8f4a-127">Примеры</span><span class="sxs-lookup"><span data-stu-id="b8f4a-127">Examples</span></span>  

 <span data-ttu-id="b8f4a-128">Приведенная ниже команда отображает все установленные на компьютере версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="b8f4a-129">Следующая команда отображает версию среды CLR, используемую процессом 128.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="b8f4a-130">Следующая команда отображает все управляемые процессы и версию среды CLR, которую они используют.</span><span class="sxs-lookup"><span data-stu-id="b8f4a-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="b8f4a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b8f4a-131">See also</span></span>

- [<span data-ttu-id="b8f4a-132">Инструменты</span><span class="sxs-lookup"><span data-stu-id="b8f4a-132">Tools</span></span>](index.md)
- [<span data-ttu-id="b8f4a-133">Командные строки</span><span class="sxs-lookup"><span data-stu-id="b8f4a-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
