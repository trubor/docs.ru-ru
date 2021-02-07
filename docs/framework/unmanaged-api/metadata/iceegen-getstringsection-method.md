---
description: 'Дополнительные сведения о методе ICeeGen:: GetStringSection'
title: Метод ICeeGen::GetStringSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: ef4b4bb502e1099b9b3bcdbd494d03df0858aa6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721064"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="a4d75-103">Метод ICeeGen::GetStringSection</span><span class="sxs-lookup"><span data-stu-id="a4d75-103">ICeeGen::GetStringSection Method</span></span>

<span data-ttu-id="a4d75-104">Возвращает строковое представление раздела кода, на который ссылается указанный маркер.</span><span class="sxs-lookup"><span data-stu-id="a4d75-104">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="a4d75-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="a4d75-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d75-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4d75-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d75-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a4d75-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="a4d75-108">[вход, выход] Маркер раздела кода.</span><span class="sxs-lookup"><span data-stu-id="a4d75-108">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d75-109">Требования</span><span class="sxs-lookup"><span data-stu-id="a4d75-109">Requirements</span></span>  

 <span data-ttu-id="a4d75-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d75-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a4d75-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4d75-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4d75-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4d75-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d75-114">См. также</span><span class="sxs-lookup"><span data-stu-id="a4d75-114">See also</span></span>

- [<span data-ttu-id="a4d75-115">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="a4d75-115">ICeeGen Interface</span></span>](iceegen-interface.md)
