---
description: 'Дополнительные сведения о: BC30955: значение типа " <typename1> " не может быть преобразовано в " <typename2> "'
title: Значение типа <typename1> невозможно привести к <typename2>
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: a013e274a1776dee6a98add63138236ad11111b8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426560"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="b449a-103">BC30955: значение типа " \<typename1> " не может быть преобразовано в " \<typename2> "</span><span class="sxs-lookup"><span data-stu-id="b449a-103">BC30955: Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>

<span data-ttu-id="b449a-104">Значение типа " \<typename1> " не может быть преобразовано в " \<typename2> ".</span><span class="sxs-lookup"><span data-stu-id="b449a-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="b449a-105">Несоответствие типов может быть вызвано смешением ссылки на файл со ссылкой проекта на сборку " \<assemblyname> ".</span><span class="sxs-lookup"><span data-stu-id="b449a-105">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="b449a-106">Попробуйте заменить ссылку на файл " \<filepath> " в проекте " \<projectname1> " ссылкой проекта на " \<projectname2> ".</span><span class="sxs-lookup"><span data-stu-id="b449a-106">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="b449a-107">В ситуации, когда проект делает ссылку на проект и ссылку на файл, компилятор не может гарантировать, что один тип можно преобразовать в другой.</span><span class="sxs-lookup"><span data-stu-id="b449a-107">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="b449a-108">В следующем псевдо-коде показана ситуация, которая может вызвать эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="b449a-108">The following pseudo-code illustrates a situation that can generate this error.</span></span>

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 <span data-ttu-id="b449a-109">Project `P1` делает косвенную ссылку на проект через проект `P2` `P3` , а также прямую ссылку на файл `P3` .</span><span class="sxs-lookup"><span data-stu-id="b449a-109">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="b449a-110">В объявлении `commonObject` используется ссылка на файл `P3` , а в вызове `P2.getCommonClass` используется ссылка на проект `P3` .</span><span class="sxs-lookup"><span data-stu-id="b449a-110">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>

 <span data-ttu-id="b449a-111">Проблема в этой ситуации заключается в том, что ссылка на файл указывает путь к файлу и имя выходного файла `P3` (обычно p3.dll), а ссылки проекта определяют исходный проект ( `P3` ) по имени проекта.</span><span class="sxs-lookup"><span data-stu-id="b449a-111">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="b449a-112">По этой причине компилятор не может гарантировать, что тип `P3.commonClass` поступает из одного и того же исходного кода через две разные ссылки.</span><span class="sxs-lookup"><span data-stu-id="b449a-112">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>

 <span data-ttu-id="b449a-113">Эта ситуация обычно возникает, если ссылки на проект и ссылки на файлы являются смешанными.</span><span class="sxs-lookup"><span data-stu-id="b449a-113">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="b449a-114">На предыдущем рисунке проблема не возникнет, если `P1` сделать прямую ссылку на проект `P3` вместо ссылки на файл.</span><span class="sxs-lookup"><span data-stu-id="b449a-114">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>

 <span data-ttu-id="b449a-115">**Идентификатор ошибки:** BC30955</span><span class="sxs-lookup"><span data-stu-id="b449a-115">**Error ID:** BC30955</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b449a-116">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="b449a-116">To correct this error</span></span>

- <span data-ttu-id="b449a-117">Измените ссылку на файл на ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="b449a-117">Change the file reference to a project reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="b449a-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b449a-118">See also</span></span>

- [<span data-ttu-id="b449a-119">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b449a-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="b449a-120">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="b449a-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
