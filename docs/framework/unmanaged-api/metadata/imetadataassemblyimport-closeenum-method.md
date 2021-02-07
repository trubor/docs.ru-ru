---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: CloseEnum'
title: Метод IMetaDataAssemblyImport::CloseEnum
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
ms.openlocfilehash: 3ff234fac905a058ed832d58a0f996a2c7393ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678085"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="a9f10-103">Метод IMetaDataAssemblyImport::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="a9f10-103">IMetaDataAssemblyImport::CloseEnum Method</span></span>

<span data-ttu-id="a9f10-104">Освобождает ссылку на указанный экземпляр перечисления.</span><span class="sxs-lookup"><span data-stu-id="a9f10-104">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f10-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a9f10-105">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9f10-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a9f10-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="a9f10-107">окне Экземпляр перечисления, который должен быть закрыт.</span><span class="sxs-lookup"><span data-stu-id="a9f10-107">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f10-108">Требования</span><span class="sxs-lookup"><span data-stu-id="a9f10-108">Requirements</span></span>  

 <span data-ttu-id="a9f10-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f10-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f10-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a9f10-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9f10-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9f10-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f10-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f10-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f10-113">См. также</span><span class="sxs-lookup"><span data-stu-id="a9f10-113">See also</span></span>

- [<span data-ttu-id="a9f10-114">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a9f10-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
