---
title: CorFlags.exe (средство преобразования CorFlags)
description: Ознакомьтесь с CorFlags.exe, средством преобразования CorFlags. Это средство позволяет настраивать раздел CorFlags заголовка переносимого исполняемого образа.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 3f9f2a71a7a33de13264ce60fa7ff6ea5832aace
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247191"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="7f033-104">CorFlags.exe (средство преобразования CorFlags)</span><span class="sxs-lookup"><span data-stu-id="7f033-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="7f033-105">Средство преобразования CorFlags позволяет настраивать раздел CorFlags в заголовке переносимого исполняемого образа.</span><span class="sxs-lookup"><span data-stu-id="7f033-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="7f033-106">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7f033-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="7f033-107">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="7f033-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="7f033-108">Дополнительные сведения см. в разделе [Командные строки](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7f033-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="7f033-109">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="7f033-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f033-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f033-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f033-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="7f033-111">Parameters</span></span>  
  
|<span data-ttu-id="7f033-112">Обязательный параметр</span><span class="sxs-lookup"><span data-stu-id="7f033-112">Required parameter</span></span>|<span data-ttu-id="7f033-113">Описание</span><span class="sxs-lookup"><span data-stu-id="7f033-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="7f033-114">Имя сборки, для которой требуется настроить раздел CorFlags.</span><span class="sxs-lookup"><span data-stu-id="7f033-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="7f033-115">Параметр</span><span class="sxs-lookup"><span data-stu-id="7f033-115">Option</span></span>|<span data-ttu-id="7f033-116">Описание</span><span class="sxs-lookup"><span data-stu-id="7f033-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="7f033-117">Устанавливает флаг 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="7f033-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="7f033-118">Снимает флаг 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="7f033-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="7f033-119">Устанавливает флаг 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="7f033-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="7f033-120">Приложение выполняется как 32-разрядный процесс даже на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="7f033-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="7f033-121">Устанавливайте этот флаг только в EXE-файлах.</span><span class="sxs-lookup"><span data-stu-id="7f033-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="7f033-122">Если флаг установлен для библиотеки DLL, она не загружается в 64-разрядных процессах и создается исключение <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="7f033-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="7f033-123">Файл EXE с этим флагом можно загрузить в 64-разрядный процесс.</span><span class="sxs-lookup"><span data-stu-id="7f033-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="7f033-124">Новые возможности .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="7f033-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="7f033-125">Снимает флаг 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="7f033-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="7f033-126">Новые возможности .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="7f033-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="7f033-127">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="7f033-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="7f033-128">Выполняет принудительное обновление, даже если сборка имеет строгое имя.</span><span class="sxs-lookup"><span data-stu-id="7f033-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="7f033-129">**Внимание!**  При обновлении сборки со строгим именем перед выполнением ее кода необходимо снова подписать сборку.</span><span class="sxs-lookup"><span data-stu-id="7f033-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="7f033-130">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="7f033-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="7f033-131">Устанавливает флаг ILONLY.</span><span class="sxs-lookup"><span data-stu-id="7f033-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="7f033-132">Снимает флаг ILONLY.</span><span class="sxs-lookup"><span data-stu-id="7f033-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="7f033-133">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="7f033-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="7f033-134">Задает версии заголовка CLR значение 2.0.</span><span class="sxs-lookup"><span data-stu-id="7f033-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="7f033-135">Обновляет версию заголовка CLR до версии 2.5.</span><span class="sxs-lookup"><span data-stu-id="7f033-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="7f033-136">**Примечание.**  Для оптимального выполнения сборок они должны иметь версию заголовка CLR 2.5.</span><span class="sxs-lookup"><span data-stu-id="7f033-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f033-137">Примечания</span><span class="sxs-lookup"><span data-stu-id="7f033-137">Remarks</span></span>  

 <span data-ttu-id="7f033-138">Если другие параметры не заданы, средство преобразования CorFlags отображает флаги заданной сборки.</span><span class="sxs-lookup"><span data-stu-id="7f033-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f033-139">См. также</span><span class="sxs-lookup"><span data-stu-id="7f033-139">See also</span></span>

- [<span data-ttu-id="7f033-140">Инструменты</span><span class="sxs-lookup"><span data-stu-id="7f033-140">Tools</span></span>](index.md)
- [<span data-ttu-id="7f033-141">64-разрядные приложения</span><span class="sxs-lookup"><span data-stu-id="7f033-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="7f033-142">Командные строки</span><span class="sxs-lookup"><span data-stu-id="7f033-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
