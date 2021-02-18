---
description: 'Дополнительные сведения: -nostdlib (Visual Basic)'
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4a00ad21bc0038a6bf42f1dd6943ccc15c1a8abb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434879"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="02ce8-103">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ce8-103">-nostdlib (Visual Basic)</span></span>

<span data-ttu-id="02ce8-104">Указывает компилятору не ссылаться автоматически на стандартные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="02ce8-104">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ce8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02ce8-105">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="02ce8-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="02ce8-106">Remarks</span></span>  

 <span data-ttu-id="02ce8-107">Параметр `-nostdlib` удаляет автоматическую ссылку на сборку System.dll и запрещает компилятору считывать файл Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="02ce8-107">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="02ce8-108">Файл Vbc.rsp, расположенный в том же каталоге, что и файл Vbc.exe, ссылается на часто используемые сборки .NET Framework и импортирует пространства имен `System` и `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="02ce8-108">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02ce8-109">При этом компилятор всегда ссылается на сборки Mscorlib.dll и Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="02ce8-109">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02ce8-110">Параметр `-nostdlib` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="02ce8-110">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ce8-111">Пример</span><span class="sxs-lookup"><span data-stu-id="02ce8-111">Example</span></span>  

 <span data-ttu-id="02ce8-112">Следующий код компилирует `T2.vb` без создания ссылок на стандартные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="02ce8-112">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="02ce8-113">Необходимо присвоить константе условной компиляции `_MYTYPE` строку Empty, чтобы удалить объект `My`.</span><span class="sxs-lookup"><span data-stu-id="02ce8-113">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="02ce8-114">См. также</span><span class="sxs-lookup"><span data-stu-id="02ce8-114">See also</span></span>

- [<span data-ttu-id="02ce8-115">-noconfig</span><span class="sxs-lookup"><span data-stu-id="02ce8-115">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="02ce8-116">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="02ce8-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="02ce8-117">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="02ce8-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="02ce8-118">Настройка доступа к объектам через My</span><span class="sxs-lookup"><span data-stu-id="02ce8-118">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
