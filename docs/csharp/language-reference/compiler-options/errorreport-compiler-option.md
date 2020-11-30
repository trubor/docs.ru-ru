---
description: -errorreport (параметры компилятора C#)
title: -errorreport (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 6238ac392ff99d18d9cc7ea07e23b08ff235c14f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173234"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="98875-103">-errorreport (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="98875-103">-errorreport (C# Compiler Options)</span></span>

<span data-ttu-id="98875-104">Этот параметр предоставляет удобный способ для сообщения о внутренней ошибке компилятора C# в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-104">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="98875-105">В Windows Vista и Windows Server 2008 параметры отчетов об ошибках, установленные в среде Visual Studio, не переопределяют параметры отчетов об ошибках Windows.</span><span class="sxs-lookup"><span data-stu-id="98875-105">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="98875-106">Параметры отчетов об ошибках Windows всегда имеют приоритет над параметрами отчетов об ошибках Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98875-106">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="98875-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98875-107">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="98875-108">Аргументы</span><span class="sxs-lookup"><span data-stu-id="98875-108">Arguments</span></span>

 <span data-ttu-id="98875-109">**Нет**</span><span class="sxs-lookup"><span data-stu-id="98875-109">**none**</span></span>  
 <span data-ttu-id="98875-110">Не будет выполняться сбор отчетов о внутренних ошибках компилятора и их отправка в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-110">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="98875-111">**prompt** Запрашивает отправку отчета при получении внутренней ошибки компилятора.</span><span class="sxs-lookup"><span data-stu-id="98875-111">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="98875-112">**prompt** является параметром по умолчанию при компиляции приложения в среде разработки.</span><span class="sxs-lookup"><span data-stu-id="98875-112">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="98875-113">**queue** Отчет об ошибке помещается в очередь.</span><span class="sxs-lookup"><span data-stu-id="98875-113">**queue** Queues the error report.</span></span> <span data-ttu-id="98875-114">При входе в систему с правами администратора можно сообщить о всех сбоях, произошедших со времени последнего входа в систему.</span><span class="sxs-lookup"><span data-stu-id="98875-114">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="98875-115">Предложение отправить отчеты об ошибках выводится не чаще одного раза в три дня.</span><span class="sxs-lookup"><span data-stu-id="98875-115">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="98875-116">**queue** является параметром по умолчанию при компиляции приложения из командной строки.</span><span class="sxs-lookup"><span data-stu-id="98875-116">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="98875-117">**send** Отчеты о внутренних ошибках компилятора автоматически отправляются в Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-117">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="98875-118">Чтобы включить этот параметр, необходимо сначала согласиться с политикой сбора данных Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-118">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="98875-119">При первом указании параметра **-errorreport:send** на компьютере отобразится сообщение компилятора с ссылкой на веб-сайт, где опубликована политика сбора данных Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-119">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="98875-120">Комментарии</span><span class="sxs-lookup"><span data-stu-id="98875-120">Remarks</span></span>

 <span data-ttu-id="98875-121">Внутренние ошибки компилятора происходят, когда компилятору не удается обработать файл исходного кода.</span><span class="sxs-lookup"><span data-stu-id="98875-121">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="98875-122">При возникновении внутренней ошибки компилятор не создает выходной файл и не предоставляет никакой полезной диагностической информации для исправления кода.</span><span class="sxs-lookup"><span data-stu-id="98875-122">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="98875-123">В предыдущих выпусках при возникновении внутренней ошибки компилятора отображалось окно с предложением сообщить о проблеме в службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="98875-123">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="98875-124">С помощью параметра **-errorreport** можно предоставить сведения о внутренней ошибке компилятора группе разработчиков Visual C#.</span><span class="sxs-lookup"><span data-stu-id="98875-124">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="98875-125">Эти отчеты об ошибках могут помочь улучшить будущие версии компилятора.</span><span class="sxs-lookup"><span data-stu-id="98875-125">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="98875-126">Возможность отправлять отчеты пользователем зависит от политики разрешений компьютера и пользователя.</span><span class="sxs-lookup"><span data-stu-id="98875-126">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="98875-127">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98875-127">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="98875-128">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="98875-128">Open the project's **Properties** page.</span></span> <span data-ttu-id="98875-129">Дополнительные сведения см. в разделе [Страница "Сборка" в конструкторе проектов (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="98875-129">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="98875-130">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="98875-130">Click the **Build** property page.</span></span>

3. <span data-ttu-id="98875-131">Нажмите кнопку **Дополнительно** .</span><span class="sxs-lookup"><span data-stu-id="98875-131">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="98875-132">Измените свойство **Отчеты о внутренних ошибках компилятора**.</span><span class="sxs-lookup"><span data-stu-id="98875-132">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="98875-133">Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="98875-133">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="98875-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="98875-134">See also</span></span>

- [<span data-ttu-id="98875-135">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="98875-135">C# Compiler Options</span></span>](./index.md)
