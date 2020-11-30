---
description: -filealign (параметры компилятора C#)
title: -filealign (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: 4b61217a3d6812ea3ab036f82d49bba05c20629e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173247"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="e6b55-103">-filealign (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="e6b55-103">-filealign (C# Compiler Options)</span></span>

<span data-ttu-id="e6b55-104">Параметр **-filealign** позволяет указать размер разделов в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="e6b55-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b55-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6b55-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6b55-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e6b55-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="e6b55-107">Значение, которое задает размер разделов в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="e6b55-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="e6b55-108">Допустимые значения: 512, 1024, 2048, 4096 и 8192.</span><span class="sxs-lookup"><span data-stu-id="e6b55-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="e6b55-109">Эти значения указаны в байтах.</span><span class="sxs-lookup"><span data-stu-id="e6b55-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6b55-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="e6b55-110">Remarks</span></span>  

 <span data-ttu-id="e6b55-111">Каждый раздел выравнивается по границе, кратной значению **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="e6b55-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="e6b55-112">Фиксированный размер по умолчанию не предусмотрен.</span><span class="sxs-lookup"><span data-stu-id="e6b55-112">There is no fixed default.</span></span> <span data-ttu-id="e6b55-113">Если значение **-filealign** не указано, среда CLR выбирает значение по умолчанию во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="e6b55-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="e6b55-114">Указанный размер раздела влияет на размер выходного файла.</span><span class="sxs-lookup"><span data-stu-id="e6b55-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="e6b55-115">Изменение размера раздела может применяться для программ, выполняющихся на небольших устройствах.</span><span class="sxs-lookup"><span data-stu-id="e6b55-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="e6b55-116">Используйте [DUMPBIN](/cpp/build/reference/dumpbin-options) для просмотра информации о разделах выходного файла.</span><span class="sxs-lookup"><span data-stu-id="e6b55-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e6b55-117">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6b55-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e6b55-118">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="e6b55-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e6b55-119">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="e6b55-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="e6b55-120">Нажмите кнопку **Дополнительно** .</span><span class="sxs-lookup"><span data-stu-id="e6b55-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="e6b55-121">Измените свойство **Выравнивание файла**.</span><span class="sxs-lookup"><span data-stu-id="e6b55-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="e6b55-122">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6b55-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b55-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e6b55-123">See also</span></span>

- [<span data-ttu-id="e6b55-124">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="e6b55-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e6b55-125">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="e6b55-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
