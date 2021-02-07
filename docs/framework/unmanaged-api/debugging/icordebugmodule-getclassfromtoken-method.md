---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Жетклассфромтокен'
title: Метод ICorDebugModule::GetClassFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
ms.openlocfilehash: 8184c6c1920a4397c4037160276b5b86033baf71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722621"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="29106-103">Метод ICorDebugModule::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="29106-103">ICorDebugModule::GetClassFromToken Method</span></span>

<span data-ttu-id="29106-104">Возвращает класс, указанный токеном метаданных.</span><span class="sxs-lookup"><span data-stu-id="29106-104">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29106-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="29106-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29106-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="29106-106">Parameters</span></span>  

 `typedef`  
 <span data-ttu-id="29106-107">окне `mdTypeDef` Токен метаданных, который ссылается на метаданные класса.</span><span class="sxs-lookup"><span data-stu-id="29106-107">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="29106-108">заполняет Указатель на адрес объекта ICorDebugClass, который представляет класс.</span><span class="sxs-lookup"><span data-stu-id="29106-108">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29106-109">Требования</span><span class="sxs-lookup"><span data-stu-id="29106-109">Requirements</span></span>  

 <span data-ttu-id="29106-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29106-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29106-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29106-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29106-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29106-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29106-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29106-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
