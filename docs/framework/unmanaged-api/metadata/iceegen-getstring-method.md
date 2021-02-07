---
description: 'Дополнительные сведения о методе ICeeGen:: GetString'
title: Метод ICeeGen::GetString
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: 227b4badff3265fc22f1c76301ba03e58fea34c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706907"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="1f759-103">Метод ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="1f759-103">ICeeGen::GetString Method</span></span>

<span data-ttu-id="1f759-104">Возвращает строку, хранящуюся по указанному относительному виртуальному адресу.</span><span class="sxs-lookup"><span data-stu-id="1f759-104">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="1f759-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="1f759-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f759-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f759-106">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f759-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="1f759-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="1f759-108">окне Относительный виртуальный адрес возвращаемой строки.</span><span class="sxs-lookup"><span data-stu-id="1f759-108">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="1f759-109">заполняет Возвращаемая строка.</span><span class="sxs-lookup"><span data-stu-id="1f759-109">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f759-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1f759-110">Requirements</span></span>  

 <span data-ttu-id="1f759-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f759-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f759-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1f759-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f759-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f759-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f759-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f759-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f759-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1f759-115">See also</span></span>

- [<span data-ttu-id="1f759-116">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="1f759-116">ICeeGen Interface</span></span>](iceegen-interface.md)
