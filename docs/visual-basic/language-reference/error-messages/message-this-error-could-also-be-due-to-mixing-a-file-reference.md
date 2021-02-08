---
description: 'Дополнительные сведения о: BC30971. <message> Эта ошибка может также быть вызвана смешением ссылки на файл со ссылкой проекта на сборку<assemblyname>'
title: <message> Эта ошибка может также быть вызвана смешением ссылки на файл и ссылки проекта на сборку <assemblyname>
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: c3b7c27c3f253389cd0a8e725ddcae3816c612b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795850"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="fabdf-103">BC30971. \<message> Эта ошибка может также быть вызвана смешением ссылки на файл со ссылкой проекта на сборку " \<assemblyname> "</span><span class="sxs-lookup"><span data-stu-id="fabdf-103">BC30971: \<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>

<span data-ttu-id="fabdf-104">\<message> Эта ошибка может также быть вызвана смешением ссылки на файл со ссылкой проекта на сборку \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="fabdf-104">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="fabdf-105">В этом случае попробуйте заменить ссылку на файл " \<assemblyfilename> " в проекте " \<projectname1> " ссылкой проекта на " \<projectname2> ".</span><span class="sxs-lookup"><span data-stu-id="fabdf-105">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="fabdf-106">Код в проекте обращается к члену другого проекта, но конфигурация решения не позволяет компилятору Visual Basic разрешить ссылку.</span><span class="sxs-lookup"><span data-stu-id="fabdf-106">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>

 <span data-ttu-id="fabdf-107">Для доступа к типу, определенному в другой сборке, компилятор Visual Basic должен иметь ссылку на эту сборку.</span><span class="sxs-lookup"><span data-stu-id="fabdf-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="fabdf-108">Это должна быть одна однозначная ссылка, не вызывающая циклических ссылок между проектами.</span><span class="sxs-lookup"><span data-stu-id="fabdf-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="fabdf-109">**Идентификатор ошибки:** BC30971</span><span class="sxs-lookup"><span data-stu-id="fabdf-109">**Error ID:** BC30971</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fabdf-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="fabdf-110">To correct this error</span></span>

1. <span data-ttu-id="fabdf-111">Определите, какой проект создает наиболее подходящую сборку для проекта, чтобы ссылаться на нее в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="fabdf-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="fabdf-112">Для этого можно использовать такие критерии, как простота доступа к файлам и частота обновления.</span><span class="sxs-lookup"><span data-stu-id="fabdf-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="fabdf-113">В свойствах проекта добавьте ссылку на проект, содержащий сборку, определяющую используемый тип.</span><span class="sxs-lookup"><span data-stu-id="fabdf-113">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="fabdf-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fabdf-114">See also</span></span>

- [<span data-ttu-id="fabdf-115">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="fabdf-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="fabdf-116">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="fabdf-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="fabdf-117">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="fabdf-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="fabdf-118">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="fabdf-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
