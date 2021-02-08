---
description: 'Дополнительные сведения о методе: Икордебугстатикфиелдсимбол:: Name'
title: Метод ICorDebugStaticFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: c74de604f5880a69b77c89e56a82ae08517dd69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794706"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="b1a92-103">Метод ICorDebugStaticFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="b1a92-103">ICorDebugStaticFieldSymbol::GetName Method</span></span>

<span data-ttu-id="b1a92-104">Получает имя статического поля.</span><span class="sxs-lookup"><span data-stu-id="b1a92-104">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a92-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1a92-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a92-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b1a92-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="b1a92-107">[in] Число символов в буфере `szName`.</span><span class="sxs-lookup"><span data-stu-id="b1a92-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b1a92-108">[out] Указатель на число символов, фактически записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="b1a92-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1a92-109">[out] Массив символов, в котором хранится возвращаемое имя.</span><span class="sxs-lookup"><span data-stu-id="b1a92-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1a92-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b1a92-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1a92-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="b1a92-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a92-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b1a92-112">Requirements</span></span>  

 <span data-ttu-id="b1a92-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a92-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a92-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1a92-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1a92-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1a92-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1a92-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a92-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a92-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b1a92-117">See also</span></span>

- [<span data-ttu-id="b1a92-118">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b1a92-118">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="b1a92-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b1a92-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
