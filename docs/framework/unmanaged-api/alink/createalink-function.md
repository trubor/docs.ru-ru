---
description: Дополнительные сведения о функции Креатеалинк
title: Функция CreateALink
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: cf34ae8d38a8339f539c770df8f5dd14e4a3e4b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638370"
---
# <a name="createalink-function"></a><span data-ttu-id="fc678-103">Функция CreateALink</span><span class="sxs-lookup"><span data-stu-id="fc678-103">CreateALink Function</span></span>

<span data-ttu-id="fc678-104">Создает экземпляр компоновщика сборок и задает указатель на указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="fc678-104">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc678-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc678-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc678-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fc678-106">Parameters</span></span>  
  
|<span data-ttu-id="fc678-107">Параметр</span><span class="sxs-lookup"><span data-stu-id="fc678-107">Parameter</span></span>|<span data-ttu-id="fc678-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fc678-108">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="fc678-109">Физическое имя одного из интерфейсов компоновщика сборок.</span><span class="sxs-lookup"><span data-stu-id="fc678-109">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="fc678-110">Расположение, которое в случае успешного завершения содержит указатель на `riid` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="fc678-110">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc678-111">Требования</span><span class="sxs-lookup"><span data-stu-id="fc678-111">Requirements</span></span>  

 <span data-ttu-id="fc678-112">**Библиотека**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="fc678-112">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc678-113">См. также</span><span class="sxs-lookup"><span data-stu-id="fc678-113">See also</span></span>

- [<span data-ttu-id="fc678-114">Al.exe (компоновщик сборок)</span><span class="sxs-lookup"><span data-stu-id="fc678-114">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
