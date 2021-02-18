---
description: 'Дополнительные сведения: -keycontainer'
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: d8b83162d9404eb2ce80e5e531457360b040f27d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436816"
---
# <a name="-keycontainer"></a><span data-ttu-id="45d67-103">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="45d67-103">-keycontainer</span></span>

<span data-ttu-id="45d67-104">Указывает имя контейнера для пары ключей, чтобы задать для сборки строгое имя.</span><span class="sxs-lookup"><span data-stu-id="45d67-104">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d67-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45d67-105">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="45d67-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="45d67-106">Arguments</span></span>  
  
|<span data-ttu-id="45d67-107">Термин</span><span class="sxs-lookup"><span data-stu-id="45d67-107">Term</span></span>|<span data-ttu-id="45d67-108">Определение</span><span class="sxs-lookup"><span data-stu-id="45d67-108">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="45d67-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="45d67-109">Required.</span></span> <span data-ttu-id="45d67-110">Файл контейнера, содержащий ключ.</span><span class="sxs-lookup"><span data-stu-id="45d67-110">Container file that contains the key.</span></span> <span data-ttu-id="45d67-111">Если имя файла содержит пробел, заключите это имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="45d67-111">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45d67-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="45d67-112">Remarks</span></span>  

 <span data-ttu-id="45d67-113">Компилятор создает компонент, который можно сделать общим, вставляя в манифест сборки открытый ключ и подписывая окончательную сборку закрытым ключом.</span><span class="sxs-lookup"><span data-stu-id="45d67-113">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="45d67-114">Чтобы создать файл ключа, в командной строке введите `sn -k file`.</span><span class="sxs-lookup"><span data-stu-id="45d67-114">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="45d67-115">Параметр `-i` устанавливает пару ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="45d67-115">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="45d67-116">Дополнительные сведения см. в статье [Sn.exe (средство строгих имен)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="45d67-116">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="45d67-117">При компиляции с параметром `-target:module` имя файла ключа сохраняется в модуле и включается в сборку, создаваемую при компиляции с параметром [-addmodule](addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="45d67-117">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="45d67-118">Этот параметр можно также указать в исходном коде любого модуля MSIL в качестве настраиваемого атрибута (<xref:System.Reflection.AssemblyKeyNameAttribute>).</span><span class="sxs-lookup"><span data-stu-id="45d67-118">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="45d67-119">Также можно передать сведения о шифровании компилятору с помощью параметра [-keyfile](keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="45d67-119">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="45d67-120">Если требуется использовать частично подписанную сборку, применяйте параметр [-delaysign](delaysign.md).</span><span class="sxs-lookup"><span data-stu-id="45d67-120">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="45d67-121">Дополнительные сведения см. в статье [Создание и использование сборок со строгими именами](../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="45d67-121">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45d67-122">Параметр `-keycontainer` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="45d67-122">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45d67-123">Пример</span><span class="sxs-lookup"><span data-stu-id="45d67-123">Example</span></span>  

 <span data-ttu-id="45d67-124">Следующий код компилирует исходный файл `Input.vb` и определяет контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="45d67-124">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="45d67-125">См. также</span><span class="sxs-lookup"><span data-stu-id="45d67-125">See also</span></span>

- [<span data-ttu-id="45d67-126">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="45d67-126">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="45d67-127">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="45d67-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="45d67-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="45d67-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="45d67-129">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="45d67-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
