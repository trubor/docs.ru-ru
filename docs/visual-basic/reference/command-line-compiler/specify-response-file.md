---
description: 'Дополнительные сведения: @ (указание файла ответов) (Visual Basic)'
title: '@ (указание файла ответа)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 7a28be0d0bf6da177d9cfe85ecdb40eccf8a339f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473918"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="8a1f1-103">@ (указание файла ответа) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a1f1-103">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="8a1f1-104">Указывает файл, содержащий параметры компилятора и файлы исходного кода, которые требуется компилировать.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-104">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a1f1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a1f1-105">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="8a1f1-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="8a1f1-106">Arguments</span></span>

`response_file`  
<span data-ttu-id="8a1f1-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-107">Required.</span></span> <span data-ttu-id="8a1f1-108">Файл, содержащий параметры компилятора и файлы исходного кода, которые требуется компилировать.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-108">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="8a1f1-109">Если имя файла содержит пробел, заключите имя файла в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="8a1f1-109">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a1f1-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="8a1f1-110">Remarks</span></span>

<span data-ttu-id="8a1f1-111">Компилятор обрабатывает параметры компилятора и файлы исходного кода, указанные в файле ответов таким образом, как если бы они были указаны в командной строке.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-111">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="8a1f1-112">Чтобы задать несколько файлов ответов для компиляции, используйте соответствующее число параметров файла ответов, таких как следующие.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-112">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="8a1f1-113">В одной строке файла ответов может содержаться несколько параметров компилятора и файлов исходного кода.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-113">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="8a1f1-114">Спецификация отдельного параметра компилятора должна размещаться на одной строке и не может разбиваться на несколько строк.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-114">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="8a1f1-115">В файл ответов можно добавлять комментарии, которые должны начинаться с символа `#`.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-115">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="8a1f1-116">Параметры, указанные в командной строке, можно объединять с параметрами, указанными в одном или нескольких файлах ответов.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-116">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="8a1f1-117">Компилятор обрабатывает параметры команд в том порядке, в котором встречает их.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-117">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="8a1f1-118">Таким образом, аргументы командной строки могут переопределять параметры, заданные ранее в файле ответов.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-118">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="8a1f1-119">Аналогично, параметры в файле ответов будут переопределять параметры, ранее заданные в командной строке или в других файлах ответов.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-119">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="8a1f1-120">В Visual Basic представлен файл Vbc.rsp, который находится в одном каталоге с файлом Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-120">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="8a1f1-121">Файл Vbc.rsp включен по умолчанию, если не используется параметр `-noconfig`.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-121">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="8a1f1-122">Дополнительные сведения см. в [-noconfig](noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="8a1f1-122">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8a1f1-123">Параметр `@` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-123">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="8a1f1-124">Пример</span><span class="sxs-lookup"><span data-stu-id="8a1f1-124">Example</span></span>

<span data-ttu-id="8a1f1-125">Ниже приведены строки из образца файла ответов.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-125">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="8a1f1-126">Пример</span><span class="sxs-lookup"><span data-stu-id="8a1f1-126">Example</span></span>

<span data-ttu-id="8a1f1-127">В следующем примере показано использование класса `@` в сочетании с файлом ответов `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="8a1f1-127">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="8a1f1-128">См. также</span><span class="sxs-lookup"><span data-stu-id="8a1f1-128">See also</span></span>

- [<span data-ttu-id="8a1f1-129">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="8a1f1-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8a1f1-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="8a1f1-130">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="8a1f1-131">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="8a1f1-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
