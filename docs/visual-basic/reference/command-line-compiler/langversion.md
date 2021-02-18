---
description: 'Дополнительные сведения: -langversion (Visual Basic)'
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 52bf910e5d6f579ec535d9de5698a8921f058002
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466865"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="40c29-103">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40c29-103">-langversion (Visual Basic)</span></span>

<span data-ttu-id="40c29-104">Инструктирует компилятор принимать только синтаксис, включенный в заданную версию языка Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40c29-104">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c29-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40c29-105">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="40c29-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="40c29-106">Arguments</span></span>

 `version`\
 <span data-ttu-id="40c29-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="40c29-107">Required.</span></span> <span data-ttu-id="40c29-108">Версия языка, используемая во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="40c29-108">The language version to be used during the compilation.</span></span> <span data-ttu-id="40c29-109">Допустимые значения: `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `16`, `default` и `latest`.</span><span class="sxs-lookup"><span data-stu-id="40c29-109">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `16`, `default` and `latest`.</span></span>

 <span data-ttu-id="40c29-110">Любое из целых чисел можно также указать, используя `.0` в качестве дополнительной версии, например `11.0`.</span><span class="sxs-lookup"><span data-stu-id="40c29-110">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="40c29-111">Чтобы просмотреть список всех возможных значений, укажите `-langversion:?` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="40c29-111">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="40c29-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="40c29-112">Remarks</span></span>

<span data-ttu-id="40c29-113">Параметр `-langversion` указывает синтаксис, принимаемый компилятором.</span><span class="sxs-lookup"><span data-stu-id="40c29-113">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="40c29-114">Например, если указать, что версия языка — 9.0, компилятор выдаст ошибки для синтаксиса, который допустим только в версии 10.0 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="40c29-114">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>

<span data-ttu-id="40c29-115">Этот параметр можно использовать при разработке приложений, предназначенных для разных версий .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40c29-115">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="40c29-116">Например, если приложение предназначено для .NET Framework 3.5, можно использовать этот параметр, чтобы не использовать синтаксис из версии языка 10.0.</span><span class="sxs-lookup"><span data-stu-id="40c29-116">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>

<span data-ttu-id="40c29-117">Задать `-langversion` напрямую можно только с помощью командной строки.</span><span class="sxs-lookup"><span data-stu-id="40c29-117">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="40c29-118">Дополнительные сведения см. в разделе [Указание конкретной версии или профиля .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="40c29-118">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>

## <a name="example"></a><span data-ttu-id="40c29-119">Пример</span><span class="sxs-lookup"><span data-stu-id="40c29-119">Example</span></span>

<span data-ttu-id="40c29-120">Следующий код компилирует `sample.vb` для Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="40c29-120">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a><span data-ttu-id="40c29-121">См. также</span><span class="sxs-lookup"><span data-stu-id="40c29-121">See also</span></span>

- [<span data-ttu-id="40c29-122">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="40c29-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="40c29-123">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="40c29-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
