---
description: 'Дополнительные сведения: -imports (Visual Basic)'
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 8c6744ff857a15da9362b724a62fcf053e9fd8f0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470204"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="d61be-103">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61be-103">-imports (Visual Basic)</span></span>

<span data-ttu-id="d61be-104">Импортирует пространства имен из указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="d61be-104">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d61be-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d61be-105">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d61be-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d61be-106">Arguments</span></span>  
  
|<span data-ttu-id="d61be-107">Термин</span><span class="sxs-lookup"><span data-stu-id="d61be-107">Term</span></span>|<span data-ttu-id="d61be-108">Определение</span><span class="sxs-lookup"><span data-stu-id="d61be-108">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="d61be-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="d61be-109">Required.</span></span> <span data-ttu-id="d61be-110">Разделенный запятыми список пространств имен для импорта.</span><span class="sxs-lookup"><span data-stu-id="d61be-110">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d61be-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="d61be-111">Remarks</span></span>  

 <span data-ttu-id="d61be-112">Параметр `-imports` импортирует любое пространство имен, определенное в текущем наборе исходных файлов или любой связанной сборке.</span><span class="sxs-lookup"><span data-stu-id="d61be-112">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="d61be-113">Элементы в пространстве имен, заданном с помощью `-imports`, доступны для всех файлов исходного кода в компиляции.</span><span class="sxs-lookup"><span data-stu-id="d61be-113">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="d61be-114">Используйте [оператор Imports (пространство имен и тип .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md), чтобы использовать пространство имен в одном файле исходного кода.</span><span class="sxs-lookup"><span data-stu-id="d61be-114">Use the [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="d61be-115">Настройка параметра -imports в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d61be-115">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d61be-116">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="d61be-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d61be-117">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="d61be-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d61be-118">2.  Перейдите на вкладку **Ссылки**.</span><span class="sxs-lookup"><span data-stu-id="d61be-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="d61be-119">3.  Введите имя пространства имен в поле рядом с кнопкой **Добавить пользовательский импорт**.</span><span class="sxs-lookup"><span data-stu-id="d61be-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="d61be-120">4.  Нажмите кнопку **Добавить пользовательский импорт**.</span><span class="sxs-lookup"><span data-stu-id="d61be-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d61be-121">Пример</span><span class="sxs-lookup"><span data-stu-id="d61be-121">Example</span></span>  

 <span data-ttu-id="d61be-122">Следующий код компилируется, когда указан параметр `-imports:system.globalization`.</span><span class="sxs-lookup"><span data-stu-id="d61be-122">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="d61be-123">В противном случае для успешной компиляции требуется, чтобы инструкция `Imports System.Globalization` была включена в начало файла исходного кода или чтобы свойство было полностью определено как `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="d61be-123">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="d61be-124">См. также</span><span class="sxs-lookup"><span data-stu-id="d61be-124">See also</span></span>

- [<span data-ttu-id="d61be-125">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="d61be-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d61be-126">Ссылки и оператор Imports</span><span class="sxs-lookup"><span data-stu-id="d61be-126">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d61be-127">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="d61be-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
