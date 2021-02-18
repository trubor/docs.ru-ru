---
description: 'Дополнительные сведения: -keyfile'
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 6d19f136d5961e8a933380164a3a77055e1da329
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466943"
---
# <a name="-keyfile"></a><span data-ttu-id="be47a-103">-keyfile</span><span class="sxs-lookup"><span data-stu-id="be47a-103">-keyfile</span></span>

<span data-ttu-id="be47a-104">Указывает файл, содержащий ключ или пару ключей, чтобы задать для сборки строгое имя.</span><span class="sxs-lookup"><span data-stu-id="be47a-104">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be47a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be47a-105">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="be47a-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="be47a-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="be47a-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="be47a-107">Required.</span></span> <span data-ttu-id="be47a-108">Файл, который содержит ключ.</span><span class="sxs-lookup"><span data-stu-id="be47a-108">File that contains the key.</span></span> <span data-ttu-id="be47a-109">Если имя файла содержит пробел, заключите это имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="be47a-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be47a-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="be47a-110">Remarks</span></span>  

 <span data-ttu-id="be47a-111">Компилятор вставляет открытый ключ в манифест сборки, а затем подписывает окончательную сборку закрытым ключом.</span><span class="sxs-lookup"><span data-stu-id="be47a-111">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="be47a-112">Чтобы создать файл ключа, в командной строке введите `sn -k file`.</span><span class="sxs-lookup"><span data-stu-id="be47a-112">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="be47a-113">Дополнительные сведения см. в статье [Sn.exe (средство строгих имен)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-113">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="be47a-114">При компиляции с параметром `-target:module` имя файла ключа сохраняется в модуле и включается в сборку, создаваемую при компиляции с параметром [-addmodule](addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-114">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="be47a-115">Также можно передать сведения о шифровании компилятору с помощью параметра [-keycontainer](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-115">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="be47a-116">Если требуется использовать частично подписанную сборку, применяйте параметр [-delaysign](delaysign.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-116">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="be47a-117">Этот параметр можно также указать в исходном коде любого модуля MSIL в качестве настраиваемого атрибута (<xref:System.Reflection.AssemblyKeyFileAttribute>).</span><span class="sxs-lookup"><span data-stu-id="be47a-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="be47a-118">Если для одной процедуры компиляции одновременно заданы параметры `-keyfile` и [-keycontainer](keycontainer.md) (в командной строке или с помощью пользовательских атрибутов), то сначала компилятор пытается использовать контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="be47a-118">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="be47a-119">В случае успеха сборка подписывается данными контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="be47a-119">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="be47a-120">Если компилятору не удастся обнаружить контейнер ключей, будет предпринята попытка использовать файл, заданный параметром `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="be47a-120">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="be47a-121">В случае успеха сборка подписывается данными из файла ключей, и эти данные о ключах помещаются в контейнер ключей (аналогично команде `sn -i`). Теперь при следующей компиляции контейнер ключей будет действителен.</span><span class="sxs-lookup"><span data-stu-id="be47a-121">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="be47a-122">Обратите внимание, что файл ключей может содержать только открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="be47a-122">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="be47a-123">Дополнительные сведения см. в статье [Создание и использование сборок со строгими именами](../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-123">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be47a-124">Параметр `-keyfile` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="be47a-124">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="be47a-125">Пример</span><span class="sxs-lookup"><span data-stu-id="be47a-125">Example</span></span>

<span data-ttu-id="be47a-126">Следующий код компилирует `Input.vb` и определяет файл ключей.</span><span class="sxs-lookup"><span data-stu-id="be47a-126">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="be47a-127">См. также</span><span class="sxs-lookup"><span data-stu-id="be47a-127">See also</span></span>

- [<span data-ttu-id="be47a-128">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="be47a-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="be47a-129">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="be47a-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="be47a-130">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be47a-130">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="be47a-131">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="be47a-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
