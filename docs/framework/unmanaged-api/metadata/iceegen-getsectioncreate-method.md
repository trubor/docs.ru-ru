---
description: 'Дополнительные сведения о методе ICeeGen:: Жетсектионкреате'
title: Метод ICeeGen::GetSectionCreate
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 2839d11c927dbf573f213d3ebaa9e6e6d8d5015d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706868"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="a2708-103">Метод ICeeGen::GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="a2708-103">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="a2708-104">Создает и получает раздел кода, используя указанные значения имени и флага.</span><span class="sxs-lookup"><span data-stu-id="a2708-104">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="a2708-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="a2708-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2708-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2708-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2708-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a2708-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="a2708-108">окне Указатель на строку, указывающую имя создаваемого раздела.</span><span class="sxs-lookup"><span data-stu-id="a2708-108">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="a2708-109">окне Флаги, указывающие параметры.</span><span class="sxs-lookup"><span data-stu-id="a2708-109">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="a2708-110">заполняет Указатель на только что созданный раздел кода.</span><span class="sxs-lookup"><span data-stu-id="a2708-110">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2708-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a2708-111">Remarks</span></span>  

 <span data-ttu-id="a2708-112">Вызывайте `GetSectionCreate` только при наличии особых требований к разделам, которые не обрабатываются другими методами.</span><span class="sxs-lookup"><span data-stu-id="a2708-112">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2708-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a2708-113">Requirements</span></span>  

 <span data-ttu-id="a2708-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2708-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2708-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a2708-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2708-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2708-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2708-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2708-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2708-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a2708-118">See also</span></span>

- [<span data-ttu-id="a2708-119">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="a2708-119">ICeeGen Interface</span></span>](iceegen-interface.md)
