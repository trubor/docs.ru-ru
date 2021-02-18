---
description: 'Дополнительные сведения: -libpath'
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: cdc3f557e0d069930032ac3b0af7a0e88762189d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455682"
---
# <a name="-libpath"></a><span data-ttu-id="27137-103">-libpath</span><span class="sxs-lookup"><span data-stu-id="27137-103">-libpath</span></span>

<span data-ttu-id="27137-104">Сообщает расположение указанных сборок.</span><span class="sxs-lookup"><span data-stu-id="27137-104">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27137-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="27137-105">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="27137-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="27137-106">Arguments</span></span>  
  
|<span data-ttu-id="27137-107">Термин</span><span class="sxs-lookup"><span data-stu-id="27137-107">Term</span></span>|<span data-ttu-id="27137-108">Определение</span><span class="sxs-lookup"><span data-stu-id="27137-108">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="27137-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="27137-109">Required.</span></span> <span data-ttu-id="27137-110">Разделенный точками с запятой список каталогов, в котором компилятор должен искать сборку, если она отсутствует как в текущем рабочем каталоге (каталоге, из которого был вызван компилятор), так и в системном каталоге среды CLR.</span><span class="sxs-lookup"><span data-stu-id="27137-110">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="27137-111">Если имя каталога содержит пробел, заключите имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="27137-111">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27137-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="27137-112">Remarks</span></span>  

 <span data-ttu-id="27137-113">Параметр `-libpath` задает расположение сборок, указанных с помощью параметра [-reference](reference.md).</span><span class="sxs-lookup"><span data-stu-id="27137-113">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="27137-114">Компилятор выполняет поиск связанных сборок, для которых не указано полное имя, в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="27137-114">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="27137-115">Текущая рабочая папка.</span><span class="sxs-lookup"><span data-stu-id="27137-115">Current working directory.</span></span> <span data-ttu-id="27137-116">Это папка, из которой был вызван компилятор.</span><span class="sxs-lookup"><span data-stu-id="27137-116">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="27137-117">Системный каталог среды CLR.</span><span class="sxs-lookup"><span data-stu-id="27137-117">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="27137-118">Каталоги, указанные параметром `-libpath`.</span><span class="sxs-lookup"><span data-stu-id="27137-118">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="27137-119">Каталоги, указанные переменной среды LIB.</span><span class="sxs-lookup"><span data-stu-id="27137-119">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="27137-120">Параметры `-libpath` является аддитивным; каждое следующее указание этого параметра присоединяется к предыдущим значениям.</span><span class="sxs-lookup"><span data-stu-id="27137-120">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="27137-121">Используйте `-reference` для указания ссылки на сборку.</span><span class="sxs-lookup"><span data-stu-id="27137-121">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="27137-122">Задание -libpath в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27137-122">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="27137-123">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="27137-123">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="27137-124">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="27137-124">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="27137-125">2.  Перейдите на вкладку **Ссылки**.</span><span class="sxs-lookup"><span data-stu-id="27137-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="27137-126">3.  Щелкните кнопку **Пути для ссылок...** .</span><span class="sxs-lookup"><span data-stu-id="27137-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="27137-127">4.  В диалоговом окне **Пути для ссылок** введите имя каталога в поле **Folder:** .</span><span class="sxs-lookup"><span data-stu-id="27137-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="27137-128">5.  Щелкните **Добавить папку**.</span><span class="sxs-lookup"><span data-stu-id="27137-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27137-129">Пример</span><span class="sxs-lookup"><span data-stu-id="27137-129">Example</span></span>  

 <span data-ttu-id="27137-130">Следующий код компилирует `T2.vb`, чтобы создать файл .exe.</span><span class="sxs-lookup"><span data-stu-id="27137-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="27137-131">Компилятор выполнит поиск ссылок на сборку в рабочем каталоге, корневом каталоге диска С и каталоге "Новые сборки" на диске C:.</span><span class="sxs-lookup"><span data-stu-id="27137-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="27137-132">См. также</span><span class="sxs-lookup"><span data-stu-id="27137-132">See also</span></span>

- [<span data-ttu-id="27137-133">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="27137-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="27137-134">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="27137-134">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="27137-135">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="27137-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
