---
description: Дополнительные сведения о перечислении КОИНИТИИ
title: Перечисление COINITIEE
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: c17980582903a29cdfe33c64200c31f29ddeb17c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678618"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="95904-103">Перечисление COINITIEE</span><span class="sxs-lookup"><span data-stu-id="95904-103">COINITIEE Enumeration</span></span>

<span data-ttu-id="95904-104">Указывает константы, используемые [CoInitialize](../hosting/coinitializeee-function.md) при инициализации среды CLR.</span><span class="sxs-lookup"><span data-stu-id="95904-104">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95904-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95904-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="95904-106">Члены</span><span class="sxs-lookup"><span data-stu-id="95904-106">Members</span></span>  
  
|<span data-ttu-id="95904-107">Член</span><span class="sxs-lookup"><span data-stu-id="95904-107">Member</span></span>|<span data-ttu-id="95904-108">Описание</span><span class="sxs-lookup"><span data-stu-id="95904-108">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="95904-109">Режим инициализации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="95904-109">Default initialization mode.</span></span> <span data-ttu-id="95904-110">Это Инициализирует среду выполнения и создает значение по умолчанию <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="95904-110">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="95904-111">Инициализирует для запуска управляемой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="95904-111">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="95904-112">Инициализирует для запуска управляемого EXE-файла.</span><span class="sxs-lookup"><span data-stu-id="95904-112">Initializes to run a managed EXE.</span></span> <span data-ttu-id="95904-113">При этом инициализируется среда выполнения, но не создается значение по умолчанию <xref:System.AppDomain> , которое создается после ввода основной подпрограммы exe-файла.</span><span class="sxs-lookup"><span data-stu-id="95904-113">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95904-114">Требования</span><span class="sxs-lookup"><span data-stu-id="95904-114">Requirements</span></span>  

 <span data-ttu-id="95904-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95904-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95904-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="95904-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95904-117">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95904-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95904-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95904-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95904-119">См. также</span><span class="sxs-lookup"><span data-stu-id="95904-119">See also</span></span>

- [<span data-ttu-id="95904-120">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="95904-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
