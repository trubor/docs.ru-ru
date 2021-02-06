---
description: 'Дополнительные сведения о: подпрограмма или функция не определена (Visual Basic)'
title: Подпрограмма или функция не определена
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 5726e8b23283b419577c468eee2344b234493425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641386"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="d8b5d-103">Sub или Function не определена (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8b5d-103">Sub or Function not defined (Visual Basic)</span></span>

<span data-ttu-id="d8b5d-104">`Sub` `Function` Для вызова необходимо определить или.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-104">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="d8b5d-105">Возможные причины этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="d8b5d-105">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="d8b5d-106">Ошибка написания имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-106">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="d8b5d-107">Попытка вызвать процедуру из другого проекта без явного добавления ссылки на этот проект в диалоговом окне " **ссылки** ".</span><span class="sxs-lookup"><span data-stu-id="d8b5d-107">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="d8b5d-108">Указание процедуры, которая не является видимой для вызывающей процедуры.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-108">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="d8b5d-109">Объявление подпрограммы библиотеки динамической компоновки Windows (DLL) или служебной программы-ресурса для Macintosh, которая не находится в указанной библиотеке или ресурсе кода.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-109">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8b5d-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d8b5d-110">To correct this error</span></span>  
  
1. <span data-ttu-id="d8b5d-111">Убедитесь, что имя процедуры написано правильно.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-111">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="d8b5d-112">Найдите имя проекта, содержащего процедуру, которую необходимо вызвать, в диалоговом окне **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="d8b5d-112">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="d8b5d-113">Если она не отображается, нажмите кнопку **Обзор** , чтобы найти ее.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-113">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="d8b5d-114">Установите флажок слева от имени проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-114">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="d8b5d-115">Проверьте имя подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="d8b5d-115">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b5d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d8b5d-116">See also</span></span>

- [<span data-ttu-id="d8b5d-117">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="d8b5d-117">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="d8b5d-118">Управление ссылками в проекте</span><span class="sxs-lookup"><span data-stu-id="d8b5d-118">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="d8b5d-119">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="d8b5d-119">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="d8b5d-120">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="d8b5d-120">Function Statement</span></span>](../statements/function-statement.md)
