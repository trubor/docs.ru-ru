---
description: 'Дополнительные сведения о методе: ICorDebugProcess6:: a Code'
title: Метод ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: a7cb71ddb1e65cda37d762a0fba958d413145138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649667"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="41562-103">Метод ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="41562-103">ICorDebugProcess6::GetCode Method</span></span>

<span data-ttu-id="41562-104">Получает информацию об управляемом коде по адресу определенного кода.</span><span class="sxs-lookup"><span data-stu-id="41562-104">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41562-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41562-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41562-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="41562-106">Parameters</span></span>  

 `codeAddress`  
 <span data-ttu-id="41562-107">окне Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , указывающее начальный адрес сегмента управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="41562-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="41562-108">заполняет Указатель на адрес объекта ICorDebugCode, который представляет сегмент управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="41562-108">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41562-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="41562-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41562-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="41562-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41562-111">Требования</span><span class="sxs-lookup"><span data-stu-id="41562-111">Requirements</span></span>  

 <span data-ttu-id="41562-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41562-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41562-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41562-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41562-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41562-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41562-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41562-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41562-116">См. также</span><span class="sxs-lookup"><span data-stu-id="41562-116">See also</span></span>

- [<span data-ttu-id="41562-117">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="41562-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="41562-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="41562-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
