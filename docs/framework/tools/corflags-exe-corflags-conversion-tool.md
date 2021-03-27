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
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="dea46-104">CorFlags.exe (средство преобразования CorFlags)</span><span class="sxs-lookup"><span data-stu-id="dea46-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="dea46-105">Средство преобразования CorFlags позволяет настраивать раздел CorFlags в заголовке переносимого исполняемого образа.</span><span class="sxs-lookup"><span data-stu-id="dea46-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="dea46-106">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dea46-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="dea46-107">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="dea46-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="dea46-108">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="dea46-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea46-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dea46-109">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea46-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="dea46-110">Parameters</span></span>  
  
|<span data-ttu-id="dea46-111">Обязательный параметр</span><span class="sxs-lookup"><span data-stu-id="dea46-111">Required parameter</span></span>|<span data-ttu-id="dea46-112">Описание</span><span class="sxs-lookup"><span data-stu-id="dea46-112">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="dea46-113">Имя сборки, для которой требуется настроить раздел CorFlags.</span><span class="sxs-lookup"><span data-stu-id="dea46-113">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="dea46-114">Параметр</span><span class="sxs-lookup"><span data-stu-id="dea46-114">Option</span></span>|<span data-ttu-id="dea46-115">Описание</span><span class="sxs-lookup"><span data-stu-id="dea46-115">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="dea46-116">Устанавливает флаг 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="dea46-116">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="dea46-117">Снимает флаг 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="dea46-117">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="dea46-118">Устанавливает флаг 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="dea46-118">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="dea46-119">Приложение выполняется как 32-разрядный процесс даже на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="dea46-119">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="dea46-120">Устанавливайте этот флаг только в EXE-файлах.</span><span class="sxs-lookup"><span data-stu-id="dea46-120">Set this flag only on EXE files.</span></span> <span data-ttu-id="dea46-121">Если флаг установлен для библиотеки DLL, она не загружается в 64-разрядных процессах и создается исключение <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="dea46-121">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="dea46-122">Файл EXE с этим флагом можно загрузить в 64-разрядный процесс.</span><span class="sxs-lookup"><span data-stu-id="dea46-122">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="dea46-123">Новые возможности .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dea46-123">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="dea46-124">Снимает флаг 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="dea46-124">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="dea46-125">Новые возможности .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dea46-125">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="dea46-126">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="dea46-126">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="dea46-127">Выполняет принудительное обновление, даже если сборка имеет строгое имя.</span><span class="sxs-lookup"><span data-stu-id="dea46-127">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="dea46-128">**Внимание!**  При обновлении сборки со строгим именем перед выполнением ее кода необходимо снова подписать сборку.</span><span class="sxs-lookup"><span data-stu-id="dea46-128">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="dea46-129">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="dea46-129">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="dea46-130">Устанавливает флаг ILONLY.</span><span class="sxs-lookup"><span data-stu-id="dea46-130">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="dea46-131">Снимает флаг ILONLY.</span><span class="sxs-lookup"><span data-stu-id="dea46-131">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="dea46-132">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="dea46-132">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="dea46-133">Задает версии заголовка CLR значение 2.0.</span><span class="sxs-lookup"><span data-stu-id="dea46-133">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="dea46-134">Обновляет версию заголовка CLR до версии 2.5.</span><span class="sxs-lookup"><span data-stu-id="dea46-134">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="dea46-135">**Примечание.**  Для оптимального выполнения сборок они должны иметь версию заголовка CLR 2.5.</span><span class="sxs-lookup"><span data-stu-id="dea46-135">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dea46-136">Примечания</span><span class="sxs-lookup"><span data-stu-id="dea46-136">Remarks</span></span>  

 <span data-ttu-id="dea46-137">Если другие параметры не заданы, средство преобразования CorFlags отображает флаги заданной сборки.</span><span class="sxs-lookup"><span data-stu-id="dea46-137">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea46-138">См. также</span><span class="sxs-lookup"><span data-stu-id="dea46-138">See also</span></span>

- [<span data-ttu-id="dea46-139">Инструменты</span><span class="sxs-lookup"><span data-stu-id="dea46-139">Tools</span></span>](index.md)
- [<span data-ttu-id="dea46-140">64-разрядные приложения</span><span class="sxs-lookup"><span data-stu-id="dea46-140">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="dea46-141">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="dea46-141">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
