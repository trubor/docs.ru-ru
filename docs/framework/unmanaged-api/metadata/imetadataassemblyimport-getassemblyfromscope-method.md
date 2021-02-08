---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: GetAssemblyFromScope'
title: Метод IMetaDataAssemblyImport::GetAssemblyFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: 78e2862fca80dc06c37436f3d81db4b19c4ec332
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784162"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="5af63-103">Метод IMetaDataAssemblyImport::GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="5af63-103">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>

<span data-ttu-id="5af63-104">Возвращает указатель на сборку в текущей области.</span><span class="sxs-lookup"><span data-stu-id="5af63-104">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af63-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5af63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5af63-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5af63-106">Parameters</span></span>  

 `ptkAssembly`  
 <span data-ttu-id="5af63-107">заполняет Указатель на полученный `mdAssembly` токен, идентифицирующий сборку.</span><span class="sxs-lookup"><span data-stu-id="5af63-107">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5af63-108">Требования</span><span class="sxs-lookup"><span data-stu-id="5af63-108">Requirements</span></span>  

 <span data-ttu-id="5af63-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5af63-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5af63-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="5af63-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5af63-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5af63-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5af63-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5af63-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af63-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5af63-113">See also</span></span>

- [<span data-ttu-id="5af63-114">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="5af63-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
