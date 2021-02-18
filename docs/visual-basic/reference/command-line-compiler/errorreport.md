---
description: 'Дополнительные сведения: -errorreport'
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6fa10482e6852a819303074b4662f02eb8d1f88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475946"
---
# <a name="-errorreport"></a><span data-ttu-id="8b503-103">-errorreport</span><span class="sxs-lookup"><span data-stu-id="8b503-103">-errorreport</span></span>

<span data-ttu-id="8b503-104">Указывает, как компилятор Visual Basic должен сообщать о внутренних ошибках компилятора.</span><span class="sxs-lookup"><span data-stu-id="8b503-104">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b503-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8b503-105">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="8b503-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="8b503-106">Remarks</span></span>

<span data-ttu-id="8b503-107">Этот параметр предоставляет удобный способ для сообщения о внутренней ошибке компилятора Visual Basic команде разработчиков Visual Basic в корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-107">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="8b503-108">По умолчанию компилятор не отправляет сведения в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-108">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="8b503-109">Однако при возникновении внутренней ошибки компилятора этот параметр позволяет сообщить о ней в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-109">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="8b503-110">Эта информация поможет инженерам Майкрософт определить причину и улучшить следующий выпуск Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b503-110">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="8b503-111">Возможность отправлять отчеты пользователем зависит от политики разрешений компьютера и пользователя.</span><span class="sxs-lookup"><span data-stu-id="8b503-111">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="8b503-112">Следующая таблица обобщает эффект параметра `-errorreport`.</span><span class="sxs-lookup"><span data-stu-id="8b503-112">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="8b503-113">Параметр</span><span class="sxs-lookup"><span data-stu-id="8b503-113">Option</span></span>|<span data-ttu-id="8b503-114">Поведение</span><span class="sxs-lookup"><span data-stu-id="8b503-114">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="8b503-115">При возникновении внутренней ошибки компилятора появляется диалоговое окно, в котором можно просмотреть точные данные, собранные компилятором.</span><span class="sxs-lookup"><span data-stu-id="8b503-115">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="8b503-116">Вы можете определить, есть ли в отчете об ошибках конфиденциальные сведения, и принять решение о том, отправлять ли его в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-116">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="8b503-117">Если вы решили отправить его, а параметры политики компьютера и пользователя это разрешают, компилятор отправляет данные в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-117">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="8b503-118">Отчет об ошибке помещается в очередь.</span><span class="sxs-lookup"><span data-stu-id="8b503-118">Queues the error report.</span></span> <span data-ttu-id="8b503-119">При входе с правами администратора можно сообщить о любых сбоях с момента последнего входа в систему (предложение отправить отчеты об ошибках будет выводиться не чаще одного раза в три дня).</span><span class="sxs-lookup"><span data-stu-id="8b503-119">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="8b503-120">Это поведение по умолчанию, если параметр `-errorreport` не указан.</span><span class="sxs-lookup"><span data-stu-id="8b503-120">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="8b503-121">Если возникает внутренняя ошибка компилятора, а параметры политики компьютера и пользователя это разрешают, компилятор отправляет данные в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-121">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="8b503-122">Параметр `-errorreport:send` пытается автоматически отправить сведения об ошибке в корпорацию Майкрософт, если отчеты включены с помощью системных параметров [Отчеты об ошибках Windows](/windows/desktop/wer/windows-error-reporting).</span><span class="sxs-lookup"><span data-stu-id="8b503-122">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="8b503-123">Если возникает внутренняя ошибка компилятора, сбор данных и их отправка в корпорацию Майкрософт выполняться не будут.</span><span class="sxs-lookup"><span data-stu-id="8b503-123">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="8b503-124">Компилятор отправляет данные, включающие стек на момент возникновения ошибки, который обычно содержит некоторый исходный код.</span><span class="sxs-lookup"><span data-stu-id="8b503-124">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="8b503-125">Если `-errorreport` используется с параметром [-bugreport](bugreport.md), то отправляется весь исходный файл.</span><span class="sxs-lookup"><span data-stu-id="8b503-125">If `-errorreport` is used with the [-bugreport](bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="8b503-126">Этот вариант лучше всего использовать с параметром [-bugreport](bugreport.md), так как он позволяет специалистам Майкрософт легче воспроизвести ошибку.</span><span class="sxs-lookup"><span data-stu-id="8b503-126">This option is best used with the [-bugreport](bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="8b503-127">Параметр `-errorreport` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="8b503-127">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="8b503-128">Пример</span><span class="sxs-lookup"><span data-stu-id="8b503-128">Example</span></span>

<span data-ttu-id="8b503-129">Следующий код пытается скомпилировать `T2.vb`, и если компилятор обнаруживает внутреннюю ошибку компилятора, он предлагает вам отправить отчет об ошибке в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8b503-129">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="8b503-130">См. также</span><span class="sxs-lookup"><span data-stu-id="8b503-130">See also</span></span>

- [<span data-ttu-id="8b503-131">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="8b503-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8b503-132">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="8b503-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="8b503-133">-bugreport</span><span class="sxs-lookup"><span data-stu-id="8b503-133">-bugreport</span></span>](bugreport.md)
