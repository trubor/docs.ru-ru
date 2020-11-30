---
description: -keycontainer (параметры компилятора C#)
title: -keycontainer (параметры компилятора C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 93ee5cd755a4fd6918d2a5825b63151a201a8f6a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91152472"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="61525-103">-keycontainer (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="61525-103">-keycontainer (C# Compiler Options)</span></span>

<span data-ttu-id="61525-104">Задает имя контейнера криптографического ключа.</span><span class="sxs-lookup"><span data-stu-id="61525-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61525-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61525-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="61525-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="61525-106">Arguments</span></span>  

 `string`  
 <span data-ttu-id="61525-107">Имя контейнера ключа строгого имени.</span><span class="sxs-lookup"><span data-stu-id="61525-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61525-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="61525-108">Remarks</span></span>  

 <span data-ttu-id="61525-109">Когда используется параметр **-keycontainer**, компилятор создает совместно используемый компонент.</span><span class="sxs-lookup"><span data-stu-id="61525-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="61525-110">Компилятор вставляет открытый ключ из указанного контейнера в манифест сборки, после чего подписывает финальную сборку закрытым ключом.</span><span class="sxs-lookup"><span data-stu-id="61525-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="61525-111">Чтобы создать файл ключа, в командной строке введите `sn -k file`.</span><span class="sxs-lookup"><span data-stu-id="61525-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="61525-112">Команда `sn -i` устанавливает пару ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="61525-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="61525-113">Этот параметр не поддерживается, когда компилятор работает на CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="61525-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="61525-114">Чтобы подписать сборку при компиляции на CoreCLR, используйте параметр [-keyfile](keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="61525-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="61525-115">При компиляции с параметром [-target:module](./target-module-compiler-option.md) имя файла ключа сохраняется в модуле и включается в сборку при компиляции этого модуля с параметром [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="61525-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="61525-116">Этот параметр можно также указать в исходном коде любого модуля MSIL в качестве настраиваемого атрибута (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="61525-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="61525-117">Также можно передать сведения о шифровании компилятору с помощью параметра [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="61525-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="61525-118">Если нужно добавить в манифест сборки открытый ключ, но при этом отложить подпись сборки до завершения ее тестирования, используйте параметр [-delaysign](./delaysign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="61525-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="61525-119">Дополнительные сведения см. в разделах [Создание и использование сборок со строгими именами](../../../standard/assembly/create-use-strong-named.md) и [Отложенная подпись сборки](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="61525-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="61525-120">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="61525-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="61525-121">Данный параметр компилятора недоступен в среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61525-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="61525-122">Программный доступ к этому параметру компилятора возможен с помощью свойства <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="61525-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61525-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="61525-123">See also</span></span>

- [<span data-ttu-id="61525-124">-keyfile (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="61525-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="61525-125">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="61525-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="61525-126">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="61525-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
