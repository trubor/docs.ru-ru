---
description: 'Дополнительные сведения о методе: ICorDebugAssembly:: Name'
title: Метод ICorDebugAssembly::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: c2ffa910eaf97c5539a33dbcd3486b7dfb117b51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711990"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="eb754-103">Метод ICorDebugAssembly::GetName</span><span class="sxs-lookup"><span data-stu-id="eb754-103">ICorDebugAssembly::GetName Method</span></span>

<span data-ttu-id="eb754-104">Возвращает имя сборки, которую `ICorDebugAssembly` представляет этот экземпляр.</span><span class="sxs-lookup"><span data-stu-id="eb754-104">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb754-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eb754-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb754-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb754-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="eb754-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="eb754-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="eb754-108">заполняет Указатель на целое число, задающее фактическую длину имени.</span><span class="sxs-lookup"><span data-stu-id="eb754-108">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="eb754-109">заполняет Массив, в котором хранится имя.</span><span class="sxs-lookup"><span data-stu-id="eb754-109">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb754-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="eb754-110">Remarks</span></span>  

 <span data-ttu-id="eb754-111">`GetName`Метод возвращает полный путь и имя файла сборки.</span><span class="sxs-lookup"><span data-stu-id="eb754-111">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb754-112">Требования</span><span class="sxs-lookup"><span data-stu-id="eb754-112">Requirements</span></span>  

 <span data-ttu-id="eb754-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb754-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb754-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb754-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb754-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb754-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb754-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb754-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
