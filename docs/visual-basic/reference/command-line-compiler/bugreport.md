---
description: 'Дополнительные сведения: -bugreport'
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 45831073121991774e462bce26040c575e0a0dc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468217"
---
# <a name="-bugreport"></a><span data-ttu-id="3e111-103">-bugreport</span><span class="sxs-lookup"><span data-stu-id="3e111-103">-bugreport</span></span>

<span data-ttu-id="3e111-104">Создает файл, который можно использовать при создании отчета об ошибках.</span><span class="sxs-lookup"><span data-stu-id="3e111-104">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e111-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e111-105">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="3e111-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3e111-106">Arguments</span></span>

|<span data-ttu-id="3e111-107">Термин</span><span class="sxs-lookup"><span data-stu-id="3e111-107">Term</span></span>|<span data-ttu-id="3e111-108">Определение</span><span class="sxs-lookup"><span data-stu-id="3e111-108">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="3e111-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="3e111-109">Required.</span></span> <span data-ttu-id="3e111-110">Имя файла, который будет содержать отчет об ошибках.</span><span class="sxs-lookup"><span data-stu-id="3e111-110">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="3e111-111">Если имя файла содержит пробел, заключите это имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="3e111-111">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e111-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="3e111-112">Remarks</span></span>

<span data-ttu-id="3e111-113">В `file` добавляются следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="3e111-113">The following information is added to `file`:</span></span>

- <span data-ttu-id="3e111-114">Копия всех файлов исходного кода, включенных в компиляцию.</span><span class="sxs-lookup"><span data-stu-id="3e111-114">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="3e111-115">Список параметров компилятора, используемых при компиляции.</span><span class="sxs-lookup"><span data-stu-id="3e111-115">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="3e111-116">Сведения о версии компилятора, среды CLR и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="3e111-116">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="3e111-117">Выходные данные компилятора (если есть).</span><span class="sxs-lookup"><span data-stu-id="3e111-117">Compiler output, if any.</span></span>

- <span data-ttu-id="3e111-118">Описание проблемы, которое нужно предоставить.</span><span class="sxs-lookup"><span data-stu-id="3e111-118">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="3e111-119">Описание предполагаемого способа решения проблемы, которое нужно предоставить.</span><span class="sxs-lookup"><span data-stu-id="3e111-119">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="3e111-120">Так как в `file` будут помещены копии всех файлов исходного кода, вам, возможно, потребуется воспроизвести предполагаемую ошибку в коде с использованием максимально короткой программы.</span><span class="sxs-lookup"><span data-stu-id="3e111-120">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e111-121">Параметр `-bugreport` позволяет создать файл, который может содержать конфиденциальную информацию.</span><span class="sxs-lookup"><span data-stu-id="3e111-121">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="3e111-122">К такой информации относится текущее время, версия компилятора, версия .NET Framework, версия ОС, имя пользователя, аргументы командной строки, с которыми был запущен компилятор, весь исходный код и двоичное представление любой базовой сборки.</span><span class="sxs-lookup"><span data-stu-id="3e111-122">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="3e111-123">Доступ к этому параметру можно получить, указав параметры командной строки в файле Web.config для компиляции приложения ASP.NET на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="3e111-123">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="3e111-124">Чтобы избежать этого, измените файл Machine.config, чтобы запретить пользователям выполнять компиляцию на сервере.</span><span class="sxs-lookup"><span data-stu-id="3e111-124">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="3e111-125">Если этот параметр используется с `-errorreport:prompt`, `-errorreport:queue` или `-errorreport:send`, а в приложении возникает внутренняя ошибка компилятора, информация из `file` отправляется в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3e111-125">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="3e111-126">Эта информация поможет инженерам Майкрософт определить причину ошибки и улучшить следующий выпуск Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e111-126">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="3e111-127">По умолчанию информация не отправляется в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3e111-127">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="3e111-128">Но при компиляции приложения с использованием `-errorreport:queue` по умолчанию приложение собирает отчеты об ошибках.</span><span class="sxs-lookup"><span data-stu-id="3e111-128">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="3e111-129">Затем, когда администратор компьютера входит в систему, система сбора информации об ошибках отобразит всплывающее окно. С его помощью администратор может отправлять в корпорацию Майкрософт любые отчеты об ошибках, возникших с момента входа в систему.</span><span class="sxs-lookup"><span data-stu-id="3e111-129">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="3e111-130">Параметр `-bugreport` не доступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="3e111-130">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="3e111-131">Пример</span><span class="sxs-lookup"><span data-stu-id="3e111-131">Example</span></span>

<span data-ttu-id="3e111-132">В следующем примере выполняется компиляция *T2.vb*. При этом все сведения об ошибках помещаются в файл *Problem.txt*.</span><span class="sxs-lookup"><span data-stu-id="3e111-132">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="3e111-133">См. также</span><span class="sxs-lookup"><span data-stu-id="3e111-133">See also</span></span>

- [<span data-ttu-id="3e111-134">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="3e111-134">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3e111-135">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e111-135">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="3e111-136">-errorreport</span><span class="sxs-lookup"><span data-stu-id="3e111-136">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="3e111-137">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="3e111-137">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="3e111-138">[Элемент trustLevel для элемента securityPolicy (схема параметров ASP.NET)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e111-138">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
