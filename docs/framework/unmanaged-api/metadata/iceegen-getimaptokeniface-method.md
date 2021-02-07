---
description: 'Дополнительные сведения о методе ICeeGen:: GetIMapTokenIface'
title: Метод ICeeGen::GetIMapTokenIface
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIMapTokenIface
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIMapTokenIface
helpviewer_keywords:
- GetIMapTokenIface method [.NET Framework metadata]
- ICeeGen::GetIMapTokenIface method [.NET Framework metadata]
ms.assetid: 847a5531-c37d-49cd-8844-9e54b5d86cf7
topic_type:
- apiref
ms.openlocfilehash: bfadcead611a8cc4e3e6117e0f0bb3635c042d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706959"
---
# <a name="iceegengetimaptokeniface-method"></a><span data-ttu-id="0fa27-103">Метод ICeeGen::GetIMapTokenIface</span><span class="sxs-lookup"><span data-stu-id="0fa27-103">ICeeGen::GetIMapTokenIface Method</span></span>

<span data-ttu-id="0fa27-104">Возвращает интерфейс, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="0fa27-104">Gets the interface referenced by the specified token.</span></span>  
  
 <span data-ttu-id="0fa27-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="0fa27-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fa27-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fa27-106">Syntax</span></span>  
  
```cpp  
HRESULT GetIMapTokenIface (  
    [in, out] IUnknown   **pIMapToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fa27-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fa27-107">Parameters</span></span>  

 `pIMapToken`  
 <span data-ttu-id="0fa27-108">[вход, выход] Токен метаданных для возвращаемого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0fa27-108">[in, out] The metadata token for the interface to be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fa27-109">Требования</span><span class="sxs-lookup"><span data-stu-id="0fa27-109">Requirements</span></span>  

 <span data-ttu-id="0fa27-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fa27-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fa27-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0fa27-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fa27-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fa27-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fa27-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fa27-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa27-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0fa27-114">See also</span></span>

- [<span data-ttu-id="0fa27-115">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0fa27-115">ICeeGen Interface</span></span>](iceegen-interface.md)
