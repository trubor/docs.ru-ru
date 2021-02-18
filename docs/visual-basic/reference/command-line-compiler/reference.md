---
description: 'Дополнительные сведения: -reference (Visual Basic)'
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: e84cdf447294a299c26a775327528a94ebba03da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474152"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="12059-103">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12059-103">-reference (Visual Basic)</span></span>

<span data-ttu-id="12059-104">Дает компилятору указание сделать всю информацию о типах из указанных сборок доступной компилируемому проекту.</span><span class="sxs-lookup"><span data-stu-id="12059-104">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12059-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12059-105">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="12059-106">or</span><span class="sxs-lookup"><span data-stu-id="12059-106">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="12059-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="12059-107">Arguments</span></span>  
  
|<span data-ttu-id="12059-108">Термин</span><span class="sxs-lookup"><span data-stu-id="12059-108">Term</span></span>|<span data-ttu-id="12059-109">Определение</span><span class="sxs-lookup"><span data-stu-id="12059-109">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="12059-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="12059-110">Required.</span></span> <span data-ttu-id="12059-111">Список всех имен файлов сборки, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="12059-111">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="12059-112">Если имя файла содержит пробел, заключите его в кавычки.</span><span class="sxs-lookup"><span data-stu-id="12059-112">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12059-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="12059-113">Remarks</span></span>  

 <span data-ttu-id="12059-114">Импортируемые файлы должны содержать метаданные сборки.</span><span class="sxs-lookup"><span data-stu-id="12059-114">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="12059-115">За пределами сборки видны только открытые типы.</span><span class="sxs-lookup"><span data-stu-id="12059-115">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="12059-116">Параметр [-addmodule](addmodule.md) импортирует метаданные из модуля.</span><span class="sxs-lookup"><span data-stu-id="12059-116">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="12059-117">При ссылке на сборку (сборка А), которая, в свою очередь, ссылается на другую сборку (сборка Б), необходимо ссылаться на сборку Б в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="12059-117">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="12059-118">Тип из сборки A наследуется из типа или реализует интерфейс сборки Б.</span><span class="sxs-lookup"><span data-stu-id="12059-118">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="12059-119">Вызывается поле, свойство, событие или метод, имеющий тип возвращаемого значения или тип параметра из сборки Б.</span><span class="sxs-lookup"><span data-stu-id="12059-119">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="12059-120">Для указания каталога, в котором находятся одна или несколько ссылок на сборки, используется параметр [-libpath](libpath.md).</span><span class="sxs-lookup"><span data-stu-id="12059-120">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="12059-121">Чтобы компилятор распознал тип в сборке (а не модуль), необходимо принудительно разрешить тип.</span><span class="sxs-lookup"><span data-stu-id="12059-121">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="12059-122">Это можно сделать различными способами, например, определив экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="12059-122">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="12059-123">Существуют другие способы разрешения имен типов в сборке для компилятора.</span><span class="sxs-lookup"><span data-stu-id="12059-123">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="12059-124">Например, при наследовании от типа в сборке имя типа будет станет известно компилятору.</span><span class="sxs-lookup"><span data-stu-id="12059-124">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="12059-125">По умолчанию используется файл ответов Vbc.rsp, который ссылается на часто используемые сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12059-125">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="12059-126">Параметр `-noconfig` позволяет запретить компилятору использовать файл Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="12059-126">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="12059-127">Краткой формой `-reference` является `-r`.</span><span class="sxs-lookup"><span data-stu-id="12059-127">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12059-128">Пример</span><span class="sxs-lookup"><span data-stu-id="12059-128">Example</span></span>  

 <span data-ttu-id="12059-129">Следующая команда компилирует исходный файл `Input.vb` и ссылочные сборки из `Metad1.dll` и `Metad2.dll` и создает файл `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="12059-129">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="12059-130">См. также</span><span class="sxs-lookup"><span data-stu-id="12059-130">See also</span></span>

- [<span data-ttu-id="12059-131">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="12059-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="12059-132">-noconfig</span><span class="sxs-lookup"><span data-stu-id="12059-132">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="12059-133">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12059-133">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="12059-134">Public</span><span class="sxs-lookup"><span data-stu-id="12059-134">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="12059-135">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="12059-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
