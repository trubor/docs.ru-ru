---
description: 'Дополнительные сведения: -baseaddress'
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: eaa2992c126ebb83b20cfdbef3ab995a30ee25fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468321"
---
# <a name="-baseaddress"></a><span data-ttu-id="787f9-103">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="787f9-103">-baseaddress</span></span>

<span data-ttu-id="787f9-104">Определяет базовый адрес по умолчанию при создании библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="787f9-104">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787f9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="787f9-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="787f9-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="787f9-106">Arguments</span></span>  
  
|<span data-ttu-id="787f9-107">Термин</span><span class="sxs-lookup"><span data-stu-id="787f9-107">Term</span></span>|<span data-ttu-id="787f9-108">Определение</span><span class="sxs-lookup"><span data-stu-id="787f9-108">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="787f9-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="787f9-109">Required.</span></span> <span data-ttu-id="787f9-110">Базовый адрес для библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="787f9-110">The base address for the DLL.</span></span> <span data-ttu-id="787f9-111">Этот адрес можно определить как десятичное, шестнадцатеричное или восьмеричное число.</span><span class="sxs-lookup"><span data-stu-id="787f9-111">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="787f9-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="787f9-112">Remarks</span></span>  

 <span data-ttu-id="787f9-113">Базовый адрес по умолчанию для библиотеки DLL задается платформой .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="787f9-113">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="787f9-114">Обратите внимание, что младшее слово этого адреса будет округляться.</span><span class="sxs-lookup"><span data-stu-id="787f9-114">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="787f9-115">Например, значение 0x11110001 округляется до 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="787f9-115">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="787f9-116">Чтобы завершить процесс подписи для библиотеки DLL, используйте параметр `–R` средства Strong Name (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="787f9-116">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="787f9-117">Этот параметр не учитывается, если целевой объект не является библиотекой DLL.</span><span class="sxs-lookup"><span data-stu-id="787f9-117">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="787f9-118">Чтобы задать параметр -baseaddress в Visual Studio IDE, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="787f9-118">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="787f9-119">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="787f9-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="787f9-120">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="787f9-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="787f9-121">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="787f9-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="787f9-122">3.  Нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="787f9-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="787f9-123">4.  Измените значение в поле **Базовый адрес DLL**.</span><span class="sxs-lookup"><span data-stu-id="787f9-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="787f9-124">**Примечание.**      Поле **Базовый адрес DLL** доступно только для чтения, если целевой объект не является библиотекой DLL.</span><span class="sxs-lookup"><span data-stu-id="787f9-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="787f9-125">См. также</span><span class="sxs-lookup"><span data-stu-id="787f9-125">See also</span></span>

- [<span data-ttu-id="787f9-126">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="787f9-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="787f9-127">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="787f9-127">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="787f9-128">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="787f9-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="787f9-129">[Sn.exe (средство Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="787f9-129">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
