---
description: Дополнительные сведения:-nologo (Visual Basic)
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 370889fbd5d4e499ba27ff8bee4adc16a7a71876
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434892"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="ff50c-103">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff50c-103">-nologo (Visual Basic)</span></span>

<span data-ttu-id="ff50c-104">Отключает отображение баннера авторских прав и информационных сообщений во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="ff50c-104">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff50c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff50c-105">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff50c-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="ff50c-106">Remarks</span></span>  

 <span data-ttu-id="ff50c-107">При указании `-nologo` компилятор не отображает баннер авторских прав.</span><span class="sxs-lookup"><span data-stu-id="ff50c-107">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="ff50c-108">По умолчанию `-nologo` не действует.</span><span class="sxs-lookup"><span data-stu-id="ff50c-108">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff50c-109">Параметр `-nologo` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="ff50c-109">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff50c-110">Пример</span><span class="sxs-lookup"><span data-stu-id="ff50c-110">Example</span></span>  

 <span data-ttu-id="ff50c-111">Следующий код компилирует `T2.vb` и не отображает баннер авторских прав.</span><span class="sxs-lookup"><span data-stu-id="ff50c-111">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff50c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="ff50c-112">See also</span></span>

- [<span data-ttu-id="ff50c-113">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="ff50c-113">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ff50c-114">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="ff50c-114">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
