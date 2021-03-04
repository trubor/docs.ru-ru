---
description: 'Дополнительные сведения о: BC30140: ошибка при создании манифеста сборки: <error message>'
title: 'Ошибка при создании манифеста сборки: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e2c690ab198e11a70a2fc3bba925ccc4ccb31c79
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103417"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a><span data-ttu-id="facee-103">BC30140: ошибка при создании манифеста сборки: \<error message></span><span class="sxs-lookup"><span data-stu-id="facee-103">BC30140: Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="facee-104">Компилятор Visual Basic вызывает компоновщик сборок (Al.exe, также известный как ALink) для создания сборки с манифестом.</span><span class="sxs-lookup"><span data-stu-id="facee-104">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="facee-105">Компоновщик сообщил об ошибке на этапе предварительного выпуска процедуры создания сборки.</span><span class="sxs-lookup"><span data-stu-id="facee-105">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>

 <span data-ttu-id="facee-106">Такая ситуация может возникнуть при наличии проблем с указанным файлом ключа или контейнером ключей.</span><span class="sxs-lookup"><span data-stu-id="facee-106">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="facee-107">Чтобы использовать для сборки полную подпись, необходимо предоставить допустимый файл ключа с информацией об открытом и закрытом ключах.</span><span class="sxs-lookup"><span data-stu-id="facee-107">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="facee-108">Чтобы использовать для сборки отложенную подпись, необходимо установить флажок **Только отложенная подпись** и предоставить допустимый файл ключа с информацией о ключах.</span><span class="sxs-lookup"><span data-stu-id="facee-108">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="facee-109">При использовании отложенной подписи для сборки наличие закрытого ключа не требуется.</span><span class="sxs-lookup"><span data-stu-id="facee-109">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="facee-110">Дополнительные сведения см. в разделе [Как подписать сборку строгим именем](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="facee-110">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

 <span data-ttu-id="facee-111">**Идентификатор ошибки:** BC30140</span><span class="sxs-lookup"><span data-stu-id="facee-111">**Error ID:** BC30140</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="facee-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="facee-112">To correct this error</span></span>

1. <span data-ttu-id="facee-113">Изучите сообщение об ошибке в кавычках и ознакомьтесь с разделом [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="facee-113">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="facee-114">дополнительные объяснения и советы по ошибке AL1019</span><span class="sxs-lookup"><span data-stu-id="facee-114">for error AL1019 further explanation and advice</span></span>

2. <span data-ttu-id="facee-115">Если ошибка не устранена, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="facee-115">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="facee-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="facee-116">See also</span></span>

- [<span data-ttu-id="facee-117">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="facee-117">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="facee-118">Страница "Подписывание" в конструкторе проектов</span><span class="sxs-lookup"><span data-stu-id="facee-118">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="facee-119">Al.exe</span><span class="sxs-lookup"><span data-stu-id="facee-119">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="facee-120">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="facee-120">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
