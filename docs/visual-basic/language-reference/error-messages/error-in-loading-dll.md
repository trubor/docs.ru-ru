---
description: 'Подробнее: ошибка при загрузке библиотеки DLL (Visual Basic)'
title: Ошибка при загрузке DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 098d05e93d328f3667000bd81290f4b77cf7949e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796513"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="fcaea-103">Ошибка при загрузке библиотеки DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcaea-103">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="fcaea-104">Библиотека динамической компоновки (DLL) — это библиотека, указанная в `Lib` предложении `Declare` инструкции.</span><span class="sxs-lookup"><span data-stu-id="fcaea-104">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="fcaea-105">Возможные причины этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="fcaea-105">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="fcaea-106">Файл не является исполняемым файлом DLL.</span><span class="sxs-lookup"><span data-stu-id="fcaea-106">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="fcaea-107">Файл не является библиотекой Microsoft Windows DLL.</span><span class="sxs-lookup"><span data-stu-id="fcaea-107">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="fcaea-108">Библиотека DLL ссылается на другую несуществующую библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="fcaea-108">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="fcaea-109">Библиотека DLL или библиотека DLL, на которую указывает ссылка, не находятся в каталоге, указанном в пути.</span><span class="sxs-lookup"><span data-stu-id="fcaea-109">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fcaea-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="fcaea-110">To correct this error</span></span>  
  
- <span data-ttu-id="fcaea-111">Если файл является исходным текстовым файлом и, следовательно, не является исполняемым DLL-файлом, он должен быть скомпилирован и связан с исполняемой формой DLL.</span><span class="sxs-lookup"><span data-stu-id="fcaea-111">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="fcaea-112">Если файл не является библиотекой Microsoft Windows DLL, получите эквивалент Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="fcaea-112">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="fcaea-113">Если библиотека DLL ссылается на другую библиотеку DLL, которая отсутствует, получите указанную библиотеку DLL и сделайте ее доступной.</span><span class="sxs-lookup"><span data-stu-id="fcaea-113">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="fcaea-114">Если библиотека DLL или библиотека DLL, на которую указывает ссылка, не находятся в каталоге, указанном в пути, переместите библиотеку DLL в каталог, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="fcaea-114">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcaea-115">См. также</span><span class="sxs-lookup"><span data-stu-id="fcaea-115">See also</span></span>

- [<span data-ttu-id="fcaea-116">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="fcaea-116">Declare Statement</span></span>](../statements/declare-statement.md)
