---
description: 'Дополнительные сведения о: BC30002: тип " <typename> " не определен'
title: Тип <typename> не определен
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 48ee0c38492769aea8c1be2e9d54eaa537e35766
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641128"
---
# <a name="bc30002-type-typename-is-not-defined"></a><span data-ttu-id="14460-103">BC30002: тип " \<typename> " не определен</span><span class="sxs-lookup"><span data-stu-id="14460-103">BC30002: Type '\<typename>' is not defined</span></span>

<span data-ttu-id="14460-104">Оператор выполнил ссылку на тип, который не был определен.</span><span class="sxs-lookup"><span data-stu-id="14460-104">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="14460-105">Тип можно определить в операторе объявления, например,, `Enum` `Structure` `Class` или `Interface` .</span><span class="sxs-lookup"><span data-stu-id="14460-105">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>

 <span data-ttu-id="14460-106">**Идентификатор ошибки:** BC30002</span><span class="sxs-lookup"><span data-stu-id="14460-106">**Error ID:** BC30002</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="14460-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="14460-107">To correct this error</span></span>

- <span data-ttu-id="14460-108">Убедитесь, что определение типа и его ссылка используют одинаковое написание.</span><span class="sxs-lookup"><span data-stu-id="14460-108">Ensure that the type definition and its reference both use the same spelling.</span></span>

- <span data-ttu-id="14460-109">Убедитесь, что определение типа доступно для ссылки.</span><span class="sxs-lookup"><span data-stu-id="14460-109">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="14460-110">Например, если тип находится в другом модуле и был объявлен `Private` , переместите определение типа в ссылающийся модуль или объявите его `Public` .</span><span class="sxs-lookup"><span data-stu-id="14460-110">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>

- <span data-ttu-id="14460-111">Убедитесь, что пространство имен типа не переопределено в проекте.</span><span class="sxs-lookup"><span data-stu-id="14460-111">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="14460-112">Если это так, используйте `Global` ключевое слово, чтобы полностью определить имя типа.</span><span class="sxs-lookup"><span data-stu-id="14460-112">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="14460-113">Например, если проект определяет пространство имен с именем `System` , доступ к этому <xref:System.Object?displayProperty=nameWithType> типу невозможен, если он не является полным с `Global` ключевым словом: `Global.System.Object` .</span><span class="sxs-lookup"><span data-stu-id="14460-113">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>

- <span data-ttu-id="14460-114">Если тип определен, но библиотека объектов или библиотека типов, в которой он определен, не зарегистрирована в Visual Basic, щелкните **Добавить ссылку** в меню **проект** , а затем выберите соответствующую библиотеку объектов или библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="14460-114">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>

- <span data-ttu-id="14460-115">Убедитесь, что тип находится в сборке, которая является частью целевого платформа .NET Framework профиля.</span><span class="sxs-lookup"><span data-stu-id="14460-115">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="14460-116">Дополнительные сведения см. в разделе [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="14460-116">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>

## <a name="see-also"></a><span data-ttu-id="14460-117">См. также</span><span class="sxs-lookup"><span data-stu-id="14460-117">See also</span></span>

- [<span data-ttu-id="14460-118">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14460-118">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="14460-119">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="14460-119">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="14460-120">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="14460-120">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="14460-121">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="14460-121">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="14460-122">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="14460-122">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="14460-123">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="14460-123">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
