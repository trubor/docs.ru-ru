---
description: 'Дополнительные сведения: отказано в разрешении (Visual Basic)'
title: В разрешении отказано
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: dcd7f69c1294d22510a3600a3feb045da30faf17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795421"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="b8c7d-103">Доступ запрещен (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8c7d-103">Permission denied (Visual Basic)</span></span>

<span data-ttu-id="b8c7d-104">Предпринята попытка записи на диск, защищенный с помощью записи, или для доступа к заблокированному файлу.</span><span class="sxs-lookup"><span data-stu-id="b8c7d-104">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8c7d-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="b8c7d-105">To correct this error</span></span>  
  
1. <span data-ttu-id="b8c7d-106">Чтобы открыть защищенный от записи файл, измените атрибут защиты записи файла.</span><span class="sxs-lookup"><span data-stu-id="b8c7d-106">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="b8c7d-107">Убедитесь, что файл не заблокирован другим процессом, и дождитесь открытия файла, пока другой процесс не выпустит его.</span><span class="sxs-lookup"><span data-stu-id="b8c7d-107">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="b8c7d-108">Чтобы получить доступ к реестру, убедитесь, что разрешения пользователя включают этот тип доступа к реестру.</span><span class="sxs-lookup"><span data-stu-id="b8c7d-108">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c7d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b8c7d-109">See also</span></span>

- [<span data-ttu-id="b8c7d-110">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="b8c7d-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
