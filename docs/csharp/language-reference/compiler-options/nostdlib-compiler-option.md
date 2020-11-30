---
description: -nostdlib (параметры компилятора C#)
title: -nostdlib (параметры компилятора C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125102"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="08071-103">-nostdlib (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="08071-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="08071-104">Параметр **-nostdlib** запрещает импорт библиотеки mscorlib.dll, которая определяет все пространство имен System.</span><span class="sxs-lookup"><span data-stu-id="08071-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="08071-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08071-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="08071-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="08071-106">Remarks</span></span>

<span data-ttu-id="08071-107">Используйте этот параметр, если вы хотите определить или создать собственное пространство имен System и объекты.</span><span class="sxs-lookup"><span data-stu-id="08071-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="08071-108">Если вы не укажете параметр **-nostdlib**, библиотека mscorlib.dll будет импортирована в вашу программу (как и при указании **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="08071-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="08071-109">Указание **-nostdlib** дает тот же результат, что и указание **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="08071-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="08071-110">Установка параметра компилятора в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08071-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="08071-111">Следующие инструкции применимы только к Visual Studio 2015 (и более ранних версий).</span><span class="sxs-lookup"><span data-stu-id="08071-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="08071-112">Свойство сборки **Не ссылаться на mscorlib.dll** отсутствует в более поздних версиях Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08071-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="08071-113">Откройте страницу **свойств** для проекта.</span><span class="sxs-lookup"><span data-stu-id="08071-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="08071-114">Щелкните страницу свойств **сборки** .</span><span class="sxs-lookup"><span data-stu-id="08071-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="08071-115">Нажмите кнопку **Дополнительно** .</span><span class="sxs-lookup"><span data-stu-id="08071-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="08071-116">Измените свойство **Не ссылаться на mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="08071-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="08071-117">Установка данного параметра компилятора программным способом</span><span class="sxs-lookup"><span data-stu-id="08071-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="08071-118">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="08071-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="08071-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="08071-119">See also</span></span>

- [<span data-ttu-id="08071-120">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="08071-120">C# Compiler Options</span></span>](./index.md)
