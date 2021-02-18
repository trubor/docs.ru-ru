---
description: 'Дополнительные сведения: -main'
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 4c225c5a0030de6de0aaa510080a586272aa920b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455669"
---
# <a name="-main"></a><span data-ttu-id="4c050-103">-main</span><span class="sxs-lookup"><span data-stu-id="4c050-103">-main</span></span>

<span data-ttu-id="4c050-104">Задает класс или модуль, содержащий процедуру `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="4c050-104">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c050-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c050-105">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c050-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="4c050-106">Arguments</span></span>  

 `location`  
 <span data-ttu-id="4c050-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="4c050-107">Required.</span></span> <span data-ttu-id="4c050-108">Имя класса или модуля, который содержит процедуру `Sub Main` для вызова при запуске программы.</span><span class="sxs-lookup"><span data-stu-id="4c050-108">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="4c050-109">Может иметь формат **-main:module** или **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="4c050-109">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c050-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="4c050-110">Remarks</span></span>  

 <span data-ttu-id="4c050-111">Используйте этот параметр при создании исполняемого файла или исполняемой программы Windows.</span><span class="sxs-lookup"><span data-stu-id="4c050-111">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="4c050-112">Если параметр **-main** опущен, компилятор ищет допустимый общедоступный объект `Sub Main` во всех открытых классах и модулях.</span><span class="sxs-lookup"><span data-stu-id="4c050-112">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="4c050-113">Описание разных форм процедуры `Main` см. в статье [о процедуре Main в Visual Basic](../../programming-guide/program-structure/main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="4c050-113">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="4c050-114">Если класс `location` наследуется от <xref:System.Windows.Forms.Form>, компилятор предоставляет стандартную процедуру `Main`, которая запускает приложение, если в классе нет процедуры `Main`.</span><span class="sxs-lookup"><span data-stu-id="4c050-114">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="4c050-115">Это позволяет компилировать код из командной строки, созданной в среде разработки.</span><span class="sxs-lookup"><span data-stu-id="4c050-115">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="4c050-116">Настройка параметра -main в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c050-116">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="4c050-117">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="4c050-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4c050-118">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="4c050-118">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="4c050-119">Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="4c050-119">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="4c050-120">Снимите флажок **Включить исполняющую среду**.</span><span class="sxs-lookup"><span data-stu-id="4c050-120">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="4c050-121">Измените значение в поле **Автоматически запускаемый объект**.</span><span class="sxs-lookup"><span data-stu-id="4c050-121">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c050-122">Пример</span><span class="sxs-lookup"><span data-stu-id="4c050-122">Example</span></span>  

 <span data-ttu-id="4c050-123">В следующем код запускается компиляция `T2.vb` и `T3.vb`, а также указано, что процедура `Sub Main` находится в классе `Test2`.</span><span class="sxs-lookup"><span data-stu-id="4c050-123">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c050-124">См. также</span><span class="sxs-lookup"><span data-stu-id="4c050-124">See also</span></span>

- [<span data-ttu-id="4c050-125">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="4c050-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4c050-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c050-126">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="4c050-127">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="4c050-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4c050-128">Процедура Main в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c050-128">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)
