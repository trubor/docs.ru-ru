---
description: 'Дополнительные сведения о методе ICeeGen:: Getilsection-'
title: Метод ICeeGen::GetIlSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: 44195ec55480279494620aed6db566f1c2308a6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707011"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="3e94b-103">Метод ICeeGen::GetIlSection</span><span class="sxs-lookup"><span data-stu-id="3e94b-103">ICeeGen::GetIlSection Method</span></span>

<span data-ttu-id="3e94b-104">Возвращает раздел базы кода промежуточного языка, на который ссылается указанный обработчик.</span><span class="sxs-lookup"><span data-stu-id="3e94b-104">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="3e94b-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="3e94b-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e94b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e94b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e94b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="3e94b-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="3e94b-108">окне Описатель для получаемого раздела.</span><span class="sxs-lookup"><span data-stu-id="3e94b-108">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e94b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3e94b-109">Requirements</span></span>  

 <span data-ttu-id="3e94b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e94b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e94b-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3e94b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e94b-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e94b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e94b-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e94b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e94b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3e94b-114">See also</span></span>

- [<span data-ttu-id="3e94b-115">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="3e94b-115">ICeeGen Interface</span></span>](iceegen-interface.md)
