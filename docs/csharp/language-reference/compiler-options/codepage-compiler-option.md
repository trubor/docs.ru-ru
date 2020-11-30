---
description: -codepage (параметры компилятора C#)
title: -codepage (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: eda4ce5604beb25ae2d72ac94fbbe7dde9695820
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91196810"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="6acbe-103">-codepage (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="6acbe-103">-codepage (C# Compiler Options)</span></span>

<span data-ttu-id="6acbe-104">Этот параметр задает кодовую страницу, используемую во время компиляции, если требуемая страница не является текущей кодовой страницей системы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6acbe-104">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6acbe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6acbe-105">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="6acbe-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="6acbe-106">Arguments</span></span>  

 `id`  
 <span data-ttu-id="6acbe-107">Идентификатор кодовой страницы, используемой для всех файлов исходного кода при компиляции.</span><span class="sxs-lookup"><span data-stu-id="6acbe-107">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6acbe-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="6acbe-108">Remarks</span></span>  

 <span data-ttu-id="6acbe-109">Во-первых, компилятор будет пытаться интерпретировать все исходные файлы в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6acbe-109">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="6acbe-110">Если кодировка файлов исходного кода отличается от UTF-8 и использует символы, отличные от 7-разрядных символов ASCII, используйте параметр **-codepage**, чтобы указать нужную кодовую страницу.</span><span class="sxs-lookup"><span data-stu-id="6acbe-110">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="6acbe-111">Параметр **-codepage** применяется ко всем файлам исходного кода, включенным в компиляцию.</span><span class="sxs-lookup"><span data-stu-id="6acbe-111">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="6acbe-112">Сведения о том, как найти кодовые страницы, которые поддерживаются в системе, см. на странице, посвященной функции [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo).</span><span class="sxs-lookup"><span data-stu-id="6acbe-112">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="6acbe-113">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="6acbe-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acbe-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6acbe-114">See also</span></span>

- [<span data-ttu-id="6acbe-115">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="6acbe-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6acbe-116">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="6acbe-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
