---
description: 'Дополнительные сведения: не удается создать необходимый временный файл'
title: Не удается создать требуемый временный файл
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 52d68b720d9f8797183cf773da45f02ceca0224d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796825"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="bec13-103">Не удается создать требуемый временный файл</span><span class="sxs-lookup"><span data-stu-id="bec13-103">Can't create necessary temporary file</span></span>

<span data-ttu-id="bec13-104">Либо диск заполнен, содержащий каталог, указанный переменной среды TEMP, либо переменная среды TEMP указывает на недопустимый диск или каталог, предназначенный только для чтения.</span><span class="sxs-lookup"><span data-stu-id="bec13-104">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bec13-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="bec13-105">To correct this error</span></span>  
  
1. <span data-ttu-id="bec13-106">Удалите файлы с диска, если они заполнены.</span><span class="sxs-lookup"><span data-stu-id="bec13-106">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="bec13-107">Укажите другой диск в переменной среды TEMP.</span><span class="sxs-lookup"><span data-stu-id="bec13-107">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="bec13-108">Укажите допустимый диск для переменной среды TEMP.</span><span class="sxs-lookup"><span data-stu-id="bec13-108">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="bec13-109">Удалите ограничение "только для чтения" из указанного диска или каталога.</span><span class="sxs-lookup"><span data-stu-id="bec13-109">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec13-110">См. также</span><span class="sxs-lookup"><span data-stu-id="bec13-110">See also</span></span>

- [<span data-ttu-id="bec13-111">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="bec13-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
