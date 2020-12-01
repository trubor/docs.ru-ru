---
title: Практическое руководство. Добавление ссылок на библиотеки типов
description: Узнайте, как добавлять ссылки на библиотеки типов в Visual Studio или для компиляции из командной строки.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 76f616c36d81b8245f77f011b5c2f9b945e6916b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255108"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="76774-103">Практическое руководство. Добавление ссылок на библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="76774-103">How to: Add References to Type Libraries</span></span>

<span data-ttu-id="76774-104">При добавлении ссылки на библиотеку типов Visual Studio генерирует сборку взаимодействия, в которой содержатся метаданные.</span><span class="sxs-lookup"><span data-stu-id="76774-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="76774-105">Если первичная сборка взаимодействия доступна, Visual Studio обращается к существующей сборке, прежде чем генерировать новую.</span><span class="sxs-lookup"><span data-stu-id="76774-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="76774-106">Добавление ссылки на библиотеку типов в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76774-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="76774-107">Если файл Windows Setup.exe не осуществит установку автоматически, установите DLL- или EXE-файл COM на компьютер.</span><span class="sxs-lookup"><span data-stu-id="76774-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="76774-108">Выберите **Проект**, **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="76774-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="76774-109">В диспетчере ссылок выберите **COM**.</span><span class="sxs-lookup"><span data-stu-id="76774-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="76774-110">Выберите библиотеку типов из списка или найдите файл с расширением .TLB.</span><span class="sxs-lookup"><span data-stu-id="76774-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="76774-111">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="76774-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="76774-112">В обозревателе решений откройте контекстное меню добавленной ссылки и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="76774-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="76774-113">Убедитесь, что в окне **Свойства** свойству **Внедрить типы взаимодействия** присвоено значение **True**.</span><span class="sxs-lookup"><span data-stu-id="76774-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="76774-114">Visual Studio внедрит информацию о типах COM в исполняемые файлы, устранив тем самым необходимость развертывать основные сборки взаимодействия в приложении.</span><span class="sxs-lookup"><span data-stu-id="76774-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76774-115">Пункты меню и параметры диалогового окна зависят от используемой версии Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76774-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="76774-116">Добавление ссылки на библиотеку типов для компиляции командной строки</span><span class="sxs-lookup"><span data-stu-id="76774-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="76774-117">Сгенерируйте сборку взаимодействия, как описано в разделе [Практическое руководство. Создание сборок взаимодействия из библиотек типов](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="76774-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="76774-118">Для внедрения информации о типах COM в исполняемые файлы используйте параметр компилятора [-link (параметры компилятора C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) или [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) с именем сборки взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="76774-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76774-119">См. также</span><span class="sxs-lookup"><span data-stu-id="76774-119">See also</span></span>

- [<span data-ttu-id="76774-120">Импорт библиотеки типов в виде сборки</span><span class="sxs-lookup"><span data-stu-id="76774-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="76774-121">Предоставление COM-компонентов платформе .NET Framework</span><span class="sxs-lookup"><span data-stu-id="76774-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="76774-122">Пошаговое руководство: Внедрение типов из управляемых сборок в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76774-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="76774-123">-link (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="76774-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="76774-124">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76774-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
