---
description: 'Дополнительные сведения о: BC30145: не удается выпустить сборку: <error message>'
title: 'Не удается выпустить сборку: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: fc3b61c80cfd3b40d802c517cdca4085bc274197
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259438"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="079f8-103">BC30145: не удалось выпустить сборку: \<error message></span><span class="sxs-lookup"><span data-stu-id="079f8-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="079f8-104">Компилятор Visual Basic вызывает компоновщик сборок (*Al.exe*, также известный как ALink) для создания сборки с манифестом, а компоновщик сообщает об ошибке на этапе эмиссии создания сборки.</span><span class="sxs-lookup"><span data-stu-id="079f8-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="079f8-105">**Идентификатор ошибки:** BC30145</span><span class="sxs-lookup"><span data-stu-id="079f8-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="079f8-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="079f8-106">To correct this error</span></span>

1. <span data-ttu-id="079f8-107">Изучите сообщение об ошибке в кавычках и ознакомьтесь с разделом [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) для получения дополнительных пояснений и рекомендаций.</span><span class="sxs-lookup"><span data-stu-id="079f8-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="079f8-108">Попробуйте подписать сборку вручную, используя [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) или [Sn.exe (средство строгих имен)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="079f8-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="079f8-109">Если ошибка не устранена, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="079f8-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="079f8-110">Подпись сборки вручную</span><span class="sxs-lookup"><span data-stu-id="079f8-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="079f8-111">Используйте [Sn.exe (средство строгих имен)](../../../framework/tools/sn-exe-strong-name-tool.md)) для создания файла пары открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="079f8-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="079f8-112">Этот файл имеет расширение *SNK* .</span><span class="sxs-lookup"><span data-stu-id="079f8-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="079f8-113">Удалите из проекта ссылку COM, вызывающую ошибку.</span><span class="sxs-lookup"><span data-stu-id="079f8-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="079f8-114">Откройте [оболочку командной строки разработчика](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="079f8-114">Open a [developer command-line shell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

4. <span data-ttu-id="079f8-115">Измените каталог на каталог, в который нужно поместить обертку сборки.</span><span class="sxs-lookup"><span data-stu-id="079f8-115">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="079f8-116">Введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="079f8-116">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="079f8-117">Пример реальной команды, которую можно ввести:</span><span class="sxs-lookup"><span data-stu-id="079f8-117">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="079f8-118">Если путь или файл содержит пробелы, используйте двойные кавычки.</span><span class="sxs-lookup"><span data-stu-id="079f8-118">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="079f8-119">В Visual Studio добавьте ссылку на сборку .NET в только что созданный файл.</span><span class="sxs-lookup"><span data-stu-id="079f8-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="079f8-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="079f8-120">See also</span></span>

- [<span data-ttu-id="079f8-121">Al.exe</span><span class="sxs-lookup"><span data-stu-id="079f8-121">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="079f8-122">Sn.exe (средство строгих имен)</span><span class="sxs-lookup"><span data-stu-id="079f8-122">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="079f8-123">Практическое руководство. Создание пары открытого и закрытого ключей</span><span class="sxs-lookup"><span data-stu-id="079f8-123">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="079f8-124">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="079f8-124">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
