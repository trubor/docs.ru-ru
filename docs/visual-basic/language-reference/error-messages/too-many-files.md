---
description: 'Дополнительные сведения: слишком много файлов'
title: Слишком много файлов
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 85d246c49f765cf618bf889d75dcc9c10b780280
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641230"
---
# <a name="too-many-files"></a><span data-ttu-id="f5772-103">Слишком много файлов</span><span class="sxs-lookup"><span data-stu-id="f5772-103">Too many files</span></span>

<span data-ttu-id="f5772-104">В корневом каталоге создано либо больше файлов, чем разрешено операционной системой, либо открыто более файлов, чем указано в параметре **Files =** в файле CONFIG.SYS.</span><span class="sxs-lookup"><span data-stu-id="f5772-104">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5772-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f5772-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f5772-106">Если программа открывает, закрывает или сохраняет файлы в корневом каталоге, измените программу так, чтобы она использовала подкаталог.</span><span class="sxs-lookup"><span data-stu-id="f5772-106">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="f5772-107">Увеличьте число файлов, указанных в параметре **Files** , в файле CONFIG.SYS и перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="f5772-107">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5772-108">См. также</span><span class="sxs-lookup"><span data-stu-id="f5772-108">See also</span></span>

- [<span data-ttu-id="f5772-109">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="f5772-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
