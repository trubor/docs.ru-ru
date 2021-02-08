---
description: 'Дополнительные сведения о: BC30969: требуется ссылка на сборку " <assemblyidentity> ", содержащую тип " <typename> ", но подходящая ссылка не может быть найдена из-за неоднозначности между проектами " <projectname1> " и "<projectname2>'
title: Требуется ссылка на сборку <assemblyidentity>, содержащую тип <typename>, но подходящую ссылку не удалось найти из-за неоднозначности между проектами <projectname1> и <projectname2>
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 945a6558ff9eea20a28bc27da27e495d0eddfb15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792041"
---
# <a name="bc30969-reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="2bf16-103">BC30969: требуется ссылка на сборку " \<assemblyidentity> ", содержащую тип " \<typename> ", но подходящая ссылка не может быть найдена из-за неоднозначности между проектами " \<projectname1> " и " \<projectname2> "</span><span class="sxs-lookup"><span data-stu-id="2bf16-103">BC30969: Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="2bf16-104">Выражение использует тип, например класс, структуру, интерфейс, перечисление или делегат, который определен за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="2bf16-104">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="2bf16-105">Однако имеются ссылки проекта на несколько сборок, определяющих этот тип.</span><span class="sxs-lookup"><span data-stu-id="2bf16-105">However, you have project references to more than one assembly defining that type.</span></span>

 <span data-ttu-id="2bf16-106">Названные проекты создают сборки с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="2bf16-106">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="2bf16-107">Поэтому компилятор не может определить, какую сборку следует использовать для типа, к которому осуществляется доступ.</span><span class="sxs-lookup"><span data-stu-id="2bf16-107">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>

 <span data-ttu-id="2bf16-108">Для доступа к типу, определенному в другой сборке, компилятор Visual Basic должен иметь ссылку на эту сборку.</span><span class="sxs-lookup"><span data-stu-id="2bf16-108">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="2bf16-109">Это должна быть одна однозначная ссылка, не вызывающая циклических ссылок между проектами.</span><span class="sxs-lookup"><span data-stu-id="2bf16-109">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="2bf16-110">**Идентификатор ошибки:** BC30969</span><span class="sxs-lookup"><span data-stu-id="2bf16-110">**Error ID:** BC30969</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2bf16-111">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="2bf16-111">To correct this error</span></span>

1. <span data-ttu-id="2bf16-112">Определите, какой проект создает наиболее подходящую сборку для проекта, чтобы ссылаться на нее в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="2bf16-112">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="2bf16-113">Для этого можно использовать такие критерии, как простота доступа к файлам и частота обновления.</span><span class="sxs-lookup"><span data-stu-id="2bf16-113">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="2bf16-114">В свойствах проекта добавьте ссылку на файл, содержащий сборку, определяющую используемый тип.</span><span class="sxs-lookup"><span data-stu-id="2bf16-114">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf16-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2bf16-115">See also</span></span>

- [<span data-ttu-id="2bf16-116">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="2bf16-116">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="2bf16-117">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="2bf16-117">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="2bf16-118">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="2bf16-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2bf16-119">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="2bf16-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
