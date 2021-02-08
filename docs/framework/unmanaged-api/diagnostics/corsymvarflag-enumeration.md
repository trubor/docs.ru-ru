---
description: Дополнительные сведения о перечислении CorSymVarFlag
title: Перечисление CorSymVarFlag
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 28f4b4775e20703e5dcaa7daf69affd3548aa3f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800465"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="b7e5c-103">Перечисление CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="b7e5c-103">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="b7e5c-104">Указывает, создается ли переменная компилятором.</span><span class="sxs-lookup"><span data-stu-id="b7e5c-104">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e5c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7e5c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b7e5c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="b7e5c-106">Members</span></span>  
  
|<span data-ttu-id="b7e5c-107">Член</span><span class="sxs-lookup"><span data-stu-id="b7e5c-107">Member</span></span>|<span data-ttu-id="b7e5c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b7e5c-108">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="b7e5c-109">Указывает, что заданная переменная создается компилятором.</span><span class="sxs-lookup"><span data-stu-id="b7e5c-109">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7e5c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b7e5c-110">Requirements</span></span>  

 <span data-ttu-id="b7e5c-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="b7e5c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e5c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="b7e5c-112">See also</span></span>

- [<span data-ttu-id="b7e5c-113">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="b7e5c-113">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
