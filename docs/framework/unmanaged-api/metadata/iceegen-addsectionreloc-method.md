---
description: 'Дополнительные сведения о методе ICeeGen:: AddSectionReloc'
title: Метод ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 715c506f0bdcb3fcef33b3e9165d1f9ae47c6073
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707180"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="4e522-103">Метод ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="4e522-103">ICeeGen::AddSectionReloc Method</span></span>

<span data-ttu-id="4e522-104">Добавляет инструкцию. reloc в базу кода.</span><span class="sxs-lookup"><span data-stu-id="4e522-104">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="4e522-105">Этот метод устарел и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="4e522-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e522-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e522-106">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e522-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4e522-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="4e522-108">окне Раздел кода в памяти, к которому добавляется инструкция. reloc.</span><span class="sxs-lookup"><span data-stu-id="4e522-108">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="4e522-109">окне Смещение раздела.</span><span class="sxs-lookup"><span data-stu-id="4e522-109">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="4e522-110">окне Раздел, на который `offset` ссылается.</span><span class="sxs-lookup"><span data-stu-id="4e522-110">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="4e522-111">окне Одно из значений [цеесектионрелоктипе](ceesectionreloctype-enumeration.md) , указывающее тип добавляемой инструкции. reloc.</span><span class="sxs-lookup"><span data-stu-id="4e522-111">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e522-112">Требования</span><span class="sxs-lookup"><span data-stu-id="4e522-112">Requirements</span></span>  

 <span data-ttu-id="4e522-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e522-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e522-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4e522-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e522-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e522-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e522-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e522-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e522-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4e522-117">See also</span></span>

- [<span data-ttu-id="4e522-118">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="4e522-118">ICeeGen Interface</span></span>](iceegen-interface.md)
