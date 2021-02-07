---
description: 'См. Дополнительные сведения о методе ICorDebugClass:: методом with Token'
title: Метод ICorDebugClass::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
ms.openlocfilehash: f87b71800410fc3a95790e6d35cf4bd10a5ce747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711541"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="e3680-103">Метод ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="e3680-103">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="e3680-104">Возвращает `TypeDef` токен метаданных, который ссылается на определение этого класса.</span><span class="sxs-lookup"><span data-stu-id="e3680-104">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3680-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3680-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3680-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3680-106">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="e3680-107">заполняет Указатель на `mdTypeDef` маркер, который ссылается на определение этого класса.</span><span class="sxs-lookup"><span data-stu-id="e3680-107">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3680-108">Требования</span><span class="sxs-lookup"><span data-stu-id="e3680-108">Requirements</span></span>  

 <span data-ttu-id="e3680-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3680-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3680-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3680-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3680-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3680-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3680-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3680-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3680-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e3680-113">See also</span></span>

- [<span data-ttu-id="e3680-114">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="e3680-114">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
