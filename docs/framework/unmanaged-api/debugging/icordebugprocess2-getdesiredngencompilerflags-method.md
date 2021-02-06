---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: GetDesiredNGENCompilerFlags'
title: Метод ICorDebugProcess2::GetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: ddc1c3a958ef42ab51d0ae06fd7ff29b13829c3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650217"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="0fd2c-103">Метод ICorDebugProcess2::GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="0fd2c-103">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="0fd2c-104">Возвращает текущие параметры флага компилятора, используемые средой CLR для выбора правильного предварительно скомпилированного (то есть машинного) образа для загрузки в этот процесс.</span><span class="sxs-lookup"><span data-stu-id="0fd2c-104">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd2c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fd2c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd2c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fd2c-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="0fd2c-107">заполняет Указатель на побитовую комбинацию значений перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) , которые используются для выбора правильного предварительно скомпилированного изображения для загрузки.</span><span class="sxs-lookup"><span data-stu-id="0fd2c-107">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd2c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0fd2c-108">Remarks</span></span>  

 <span data-ttu-id="0fd2c-109">Используйте метод [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) , чтобы задать флаги, которые среда CLR будет использовать для выбора правильного предварительно скомпилированного изображения для загрузки.</span><span class="sxs-lookup"><span data-stu-id="0fd2c-109">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd2c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0fd2c-110">Requirements</span></span>  

 <span data-ttu-id="0fd2c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd2c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd2c-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fd2c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fd2c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fd2c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd2c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
