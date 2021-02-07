---
description: 'Дополнительные сведения о методе: ICorDebugAssembly3:: EnumerateContainedAssemblies'
title: Метод ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 8933500713661ef785eb3ce5abc574e512580b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754086"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="528b0-103">Метод ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="528b0-103">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>

<span data-ttu-id="528b0-104">Получает перечислитель для сборок, содержащихся в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="528b0-104">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528b0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="528b0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="528b0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="528b0-106">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="528b0-107">[выходной] Указатель на адрес объекта интерфейса ICorDebugAssemblyEnum, который является перечислителем.</span><span class="sxs-lookup"><span data-stu-id="528b0-107">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="528b0-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="528b0-108">Return Value</span></span>  

 <span data-ttu-id="528b0-109">`S_OK`, если этот объект `ICorDebugAssembly3` является контейнером; в противном случае — `S_FALSE`, и перечисление будет пустым.</span><span class="sxs-lookup"><span data-stu-id="528b0-109">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="528b0-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="528b0-110">Remarks</span></span>  

 <span data-ttu-id="528b0-111">Символы необходимы для перечисления вложенных сборок.</span><span class="sxs-lookup"><span data-stu-id="528b0-111">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="528b0-112">Если они отсутствуют, метод возвращает `S_FALSE`, и действительный перечислитель отсутствует.</span><span class="sxs-lookup"><span data-stu-id="528b0-112">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="528b0-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="528b0-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="528b0-114">Требования</span><span class="sxs-lookup"><span data-stu-id="528b0-114">Requirements</span></span>  

 <span data-ttu-id="528b0-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="528b0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="528b0-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="528b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="528b0-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="528b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="528b0-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="528b0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528b0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="528b0-119">See also</span></span>

- [<span data-ttu-id="528b0-120">Интерфейс ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="528b0-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="528b0-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="528b0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
