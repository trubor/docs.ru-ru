---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинемесодимпл'
title: Метод IMetaDataEmit::DefineMethodImpl
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 9c79d713e61bfcc7b3191e570ed727b128422bf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753410"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="fb1b3-103">Метод IMetaDataEmit::DefineMethodImpl</span><span class="sxs-lookup"><span data-stu-id="fb1b3-103">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="fb1b3-104">Создает определение для реализации метода, унаследованного от интерфейса, и возвращает маркер для этого определения реализации метода.</span><span class="sxs-lookup"><span data-stu-id="fb1b3-104">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1b3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb1b3-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb1b3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fb1b3-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="fb1b3-107">окне `mdTypedef` Токен реализующего класса.</span><span class="sxs-lookup"><span data-stu-id="fb1b3-107">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="fb1b3-108">окне `mdMethodDef` Токен или `mdMemberRef` тела кода.</span><span class="sxs-lookup"><span data-stu-id="fb1b3-108">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="fb1b3-109">окне `mdMethodDef` Токен или `mdMemberRef` реализуемого метода интерфейса.</span><span class="sxs-lookup"><span data-stu-id="fb1b3-109">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb1b3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="fb1b3-110">Requirements</span></span>  

 <span data-ttu-id="fb1b3-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb1b3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb1b3-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="fb1b3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb1b3-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb1b3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb1b3-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb1b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1b3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="fb1b3-115">See also</span></span>

- [<span data-ttu-id="fb1b3-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fb1b3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fb1b3-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fb1b3-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
