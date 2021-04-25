---
description: 'Дополнительные сведения: -subsystemversion (Visual Basic)'
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 5cb4c79b3f837e2427f1b76e7f49ed0bcec596dd
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494068"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="d55bd-103">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d55bd-103">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="d55bd-104">Указывает минимальную версию подсистемы, в которой может выполняться созданный исполняемый файл, то есть определяет версии Windows, в которых может работать исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="d55bd-104">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="d55bd-105">Чаще всего этот параметр предоставляет исполняемому файлу возможность использовать определенные возможности безопасности, недоступные в прежних версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="d55bd-105">Most commonly, this option ensures that the executable file can leverage particular security features that aren't available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="d55bd-106">Чтобы задать саму подсистему, используйте параметр компилятора [-target](target.md).</span><span class="sxs-lookup"><span data-stu-id="d55bd-106">To specify the subsystem itself, use the [-target](target.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="d55bd-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d55bd-107">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="d55bd-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="d55bd-108">Parameters</span></span>

`major.minor`

<span data-ttu-id="d55bd-109">Минимальная требуемая версия подсистемы, через точку записывается основная и дополнительная версии.</span><span class="sxs-lookup"><span data-stu-id="d55bd-109">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="d55bd-110">Например, можно указать, что приложение не может выполняться в операционной системе старше Windows 7, если задать для этого параметра значение 6.01, как указано в таблице ниже в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d55bd-110">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="d55bd-111">Необходимо указать значения для параметра `major` и `minor` в виде целых чисел.</span><span class="sxs-lookup"><span data-stu-id="d55bd-111">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="d55bd-112">Нули в начале версии `minor` не изменяют версию, нули в конце — изменяют.</span><span class="sxs-lookup"><span data-stu-id="d55bd-112">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="d55bd-113">Например, 6.1 и 6.01 — одна версия, а 6.10 — другая.</span><span class="sxs-lookup"><span data-stu-id="d55bd-113">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="d55bd-114">Рекомендуется указывать дополнительный номер версии двумя цифрами, чтобы избежать путаницы.</span><span class="sxs-lookup"><span data-stu-id="d55bd-114">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="d55bd-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="d55bd-115">Remarks</span></span>

<span data-ttu-id="d55bd-116">В следующей таблице перечислены распространенные версии подсистем Windows.</span><span class="sxs-lookup"><span data-stu-id="d55bd-116">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="d55bd-117">Версия Windows</span><span class="sxs-lookup"><span data-stu-id="d55bd-117">Windows version</span></span>|<span data-ttu-id="d55bd-118">Версия подсистемы</span><span class="sxs-lookup"><span data-stu-id="d55bd-118">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="d55bd-119">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="d55bd-119">Windows Server 2003</span></span>|<span data-ttu-id="d55bd-120">5.02</span><span class="sxs-lookup"><span data-stu-id="d55bd-120">5.02</span></span>|
|<span data-ttu-id="d55bd-121">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="d55bd-121">Windows Vista</span></span>|<span data-ttu-id="d55bd-122">6.00</span><span class="sxs-lookup"><span data-stu-id="d55bd-122">6.00</span></span>|
|<span data-ttu-id="d55bd-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="d55bd-123">Windows 7</span></span>|<span data-ttu-id="d55bd-124">6.01</span><span class="sxs-lookup"><span data-stu-id="d55bd-124">6.01</span></span>|
|<span data-ttu-id="d55bd-125">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="d55bd-125">Windows Server 2008</span></span>|<span data-ttu-id="d55bd-126">6.01</span><span class="sxs-lookup"><span data-stu-id="d55bd-126">6.01</span></span>|
|<span data-ttu-id="d55bd-127">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d55bd-127">Windows 8</span></span>|<span data-ttu-id="d55bd-128">6.02</span><span class="sxs-lookup"><span data-stu-id="d55bd-128">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="d55bd-129">Значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d55bd-129">Default values</span></span>

<span data-ttu-id="d55bd-130">Значение по умолчанию параметра компилятора **-subsystemversion** зависит от условий в следующем списке:</span><span class="sxs-lookup"><span data-stu-id="d55bd-130">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="d55bd-131">Значение по умолчанию — 6.02, если задан любой параметр компилятора из следующего списка.</span><span class="sxs-lookup"><span data-stu-id="d55bd-131">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="d55bd-132">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="d55bd-132">-target:appcontainerexe</span></span>](target.md)

  - [<span data-ttu-id="d55bd-133">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="d55bd-133">-target:winmdobj</span></span>](target.md)

  - [<span data-ttu-id="d55bd-134">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="d55bd-134">-platform:arm</span></span>](platform.md)

- <span data-ttu-id="d55bd-135">Значение по умолчанию — 6.00, если используется средство MSBuild, приложение предназначено для .NET Framework 4.5 и не установлены параметры компилятора, определенные ранее в этом списке.</span><span class="sxs-lookup"><span data-stu-id="d55bd-135">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="d55bd-136">Если ни одно из предыдущих условий не верно, значение по умолчанию — 4.00.</span><span class="sxs-lookup"><span data-stu-id="d55bd-136">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="d55bd-137">Задание этого параметра</span><span class="sxs-lookup"><span data-stu-id="d55bd-137">Setting this option</span></span>

<span data-ttu-id="d55bd-138">Чтобы задать параметр компилятора **-subsystemversion** в Visual Studio, нужно открыть файл .vbproj и указать значение для свойства `SubsystemVersion` в XML MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d55bd-138">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="d55bd-139">Этот параметр невозможно задать в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d55bd-139">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="d55bd-140">Дополнительные сведения см. выше в подразделе "Значения по умолчанию" или в разделе [Общие свойства проектов MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="d55bd-140">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="d55bd-141">См. также</span><span class="sxs-lookup"><span data-stu-id="d55bd-141">See also</span></span>

- [<span data-ttu-id="d55bd-142">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="d55bd-142">Visual Basic Command-Line Compiler</span></span>](index.md)

- [<span data-ttu-id="d55bd-143">Свойства MSBuild</span><span class="sxs-lookup"><span data-stu-id="d55bd-143">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
