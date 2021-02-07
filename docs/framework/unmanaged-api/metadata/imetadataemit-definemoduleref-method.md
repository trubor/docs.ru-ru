---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинемодулереф'
title: Метод IMetaDataEmit::DefineModuleRef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: b5af5e458f749d2315612bbe9419f037331f8c46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753397"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="55d79-103">Метод IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="55d79-103">IMetaDataEmit::DefineModuleRef Method</span></span>

<span data-ttu-id="55d79-104">Создает подпись метаданных для модуля с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="55d79-104">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d79-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55d79-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55d79-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="55d79-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="55d79-107">окне Имя другого файла метаданных, обычно DLL.</span><span class="sxs-lookup"><span data-stu-id="55d79-107">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="55d79-108">Это только имя файла.</span><span class="sxs-lookup"><span data-stu-id="55d79-108">This is the file name only.</span></span> <span data-ttu-id="55d79-109">Не используйте полное имя пути.</span><span class="sxs-lookup"><span data-stu-id="55d79-109">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="55d79-110">заполняет Назначенный `mdModuleRef` маркер.</span><span class="sxs-lookup"><span data-stu-id="55d79-110">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55d79-111">Требования</span><span class="sxs-lookup"><span data-stu-id="55d79-111">Requirements</span></span>  

 <span data-ttu-id="55d79-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55d79-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55d79-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="55d79-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55d79-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55d79-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55d79-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55d79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d79-116">См. также</span><span class="sxs-lookup"><span data-stu-id="55d79-116">See also</span></span>

- [<span data-ttu-id="55d79-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="55d79-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="55d79-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="55d79-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
