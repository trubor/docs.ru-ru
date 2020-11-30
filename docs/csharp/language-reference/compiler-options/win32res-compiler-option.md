---
description: -win32res (параметры компилятора C#)
title: -win32res (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 442c788595a01db9c0a1196d9e13b2a98963a38c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91204350"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="c77cb-103">-win32res (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="c77cb-103">-win32res (C# Compiler Options)</span></span>

<span data-ttu-id="c77cb-104">Параметр **-win32res** вставляет ресурс Win32 в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="c77cb-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c77cb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c77cb-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c77cb-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="c77cb-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="c77cb-107">Файл ресурсов, который требуется добавить в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="c77cb-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c77cb-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c77cb-108">Remarks</span></span>  

 <span data-ttu-id="c77cb-109">Файл ресурсов Win32 можно создать с помощью [компилятора ресурсов](resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c77cb-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="c77cb-110">Компилятор ресурсов вызывается при компиляции программы Visual C++; RES-файл создается из RC-файла.</span><span class="sxs-lookup"><span data-stu-id="c77cb-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="c77cb-111">Ресурс Win32 может содержать сведения о версии или точечный рисунок (значок) для упрощения идентификации приложения в проводнике.</span><span class="sxs-lookup"><span data-stu-id="c77cb-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="c77cb-112">Если параметр **-win32res** не задан, компилятор будет создавать сведения о версии на основе версии сборки.</span><span class="sxs-lookup"><span data-stu-id="c77cb-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="c77cb-113">Дополнительные сведения о ссылках на файлы ресурсов .NET Framework и их присоединении см. в разделах [-linkresource](./linkresource-compiler-option.md) и [-resource](./resource-compiler-option.md) соответственно.</span><span class="sxs-lookup"><span data-stu-id="c77cb-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c77cb-114">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c77cb-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c77cb-115">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="c77cb-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c77cb-116">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="c77cb-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="c77cb-117">Чтобы выбрать файл в поле со списком, нажмите кнопку **Файл ресурсов**.</span><span class="sxs-lookup"><span data-stu-id="c77cb-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c77cb-118">Пример</span><span class="sxs-lookup"><span data-stu-id="c77cb-118">Example</span></span>  

 <span data-ttu-id="c77cb-119">Скомпилируйте `in.cs` и присоедините файл ресурсов Win32 `rf.res`, чтобы создать `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="c77cb-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c77cb-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c77cb-120">See also</span></span>

- [<span data-ttu-id="c77cb-121">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="c77cb-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c77cb-122">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="c77cb-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
