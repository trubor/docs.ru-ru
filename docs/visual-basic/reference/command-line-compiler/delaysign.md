---
description: 'Дополнительные сведения: -delaysign'
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: fc3e52f63431da870355e369e6ffeb8b7b14c5ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461506"
---
# <a name="-delaysign"></a><span data-ttu-id="07749-103">-delaysign</span><span class="sxs-lookup"><span data-stu-id="07749-103">-delaysign</span></span>

<span data-ttu-id="07749-104">Указывает, будет ли сборка полностью или частично подписана.</span><span class="sxs-lookup"><span data-stu-id="07749-104">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="07749-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07749-105">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="07749-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="07749-106">Arguments</span></span>

<span data-ttu-id="07749-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="07749-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="07749-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="07749-108">Optional.</span></span> <span data-ttu-id="07749-109">Если требуется полностью подписанная сборка, используйте `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="07749-109">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="07749-110">Используйте `-delaysign+`, если необходимо поместить открытый ключ в сборку и зарезервировать пространство для подписанного хэша.</span><span class="sxs-lookup"><span data-stu-id="07749-110">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="07749-111">Значение по умолчанию — `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="07749-111">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="07749-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="07749-112">Remarks</span></span>

<span data-ttu-id="07749-113">Параметр `-delaysign` не имеет никакого эффекта, если вместе с ним не указан параметр [-keyfile](keyfile.md) или [-keycontainer](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="07749-113">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="07749-114">При запросе полностью подписанной сборки компилятор хэширует файл, содержащий манифест (метаданные сборки), и подписывает хэш закрытым ключом.</span><span class="sxs-lookup"><span data-stu-id="07749-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="07749-115">Итоговая цифровая подпись хранится в файле, содержащем манифест.</span><span class="sxs-lookup"><span data-stu-id="07749-115">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="07749-116">При использовании отложенной подписи компилятор не вычисляет и не сохраняет подпись, а резервирует место в файле для добавления подписи в сборку в будущем.</span><span class="sxs-lookup"><span data-stu-id="07749-116">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="07749-117">Например, с помощью `-delaysign+` разработчик в организации может распространять неподписанные тестовые версии сборки, которые тест-инженеры могут зарегистрировать в глобальном кэше сборок и впоследствии использовать.</span><span class="sxs-lookup"><span data-stu-id="07749-117">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="07749-118">После завершения работы над сборкой лицо, ответственное за закрытый ключ организации, может полностью подписать сборку.</span><span class="sxs-lookup"><span data-stu-id="07749-118">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="07749-119">Такая схема защищает закрытый ключ организации от раскрытия и при этом позволяет всем разработчикам работать со сборками.</span><span class="sxs-lookup"><span data-stu-id="07749-119">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="07749-120">Дополнительные сведения см. в статье [Создание и использование сборок со строгими именами](../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="07749-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="07749-121">Задание параметра -delaysign в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="07749-121">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="07749-122">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="07749-122">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="07749-123">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="07749-123">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="07749-124">Откройте вкладку **Подписывание**.</span><span class="sxs-lookup"><span data-stu-id="07749-124">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="07749-125">Задайте значение в поле **Только отложенная подпись**.</span><span class="sxs-lookup"><span data-stu-id="07749-125">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="07749-126">См. также</span><span class="sxs-lookup"><span data-stu-id="07749-126">See also</span></span>

- [<span data-ttu-id="07749-127">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="07749-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="07749-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="07749-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="07749-129">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="07749-129">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="07749-130">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="07749-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
