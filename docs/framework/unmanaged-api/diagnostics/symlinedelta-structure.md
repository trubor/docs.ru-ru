---
description: 'Дополнительные сведения о: структура SYMLINEDELTA'
title: Структура SYMLINEDELTA
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: ae00d2be9809b48180d2cd99d05e410624033419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761451"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="00d9f-103">Структура SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="00d9f-103">SYMLINEDELTA Structure</span></span>

<span data-ttu-id="00d9f-104">Предоставляет сведения обработчику символов о методах, которые были перемещены в результате изменений.</span><span class="sxs-lookup"><span data-stu-id="00d9f-104">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d9f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00d9f-105">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="00d9f-106">Члены</span><span class="sxs-lookup"><span data-stu-id="00d9f-106">Members</span></span>  
  
|<span data-ttu-id="00d9f-107">Член</span><span class="sxs-lookup"><span data-stu-id="00d9f-107">Member</span></span>|<span data-ttu-id="00d9f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="00d9f-108">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="00d9f-109">Токен метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="00d9f-109">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="00d9f-110">Число строк, в которые был перемещен метод.</span><span class="sxs-lookup"><span data-stu-id="00d9f-110">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00d9f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="00d9f-111">Requirements</span></span>  

 <span data-ttu-id="00d9f-112">**Заголовок:** Корсим. idl</span><span class="sxs-lookup"><span data-stu-id="00d9f-112">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d9f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="00d9f-113">See also</span></span>

- [<span data-ttu-id="00d9f-114">Структуры хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="00d9f-114">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
