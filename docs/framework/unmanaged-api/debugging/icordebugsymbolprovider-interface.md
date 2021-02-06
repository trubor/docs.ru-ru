---
description: 'Дополнительные сведения о: интерфейс метод icordebugsymbolprovider'
title: Интерфейс ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: bd47f294092ee87fc1f34bc68fe744b447e21f20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659586"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="6e747-103">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="6e747-103">ICorDebugSymbolProvider Interface</span></span>

<span data-ttu-id="6e747-104">Предоставляет методы, которые могут использоваться для получения сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="6e747-104">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e747-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6e747-105">Methods</span></span>  
  
|<span data-ttu-id="6e747-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6e747-106">Method</span></span>|<span data-ttu-id="6e747-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6e747-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e747-108">Метод GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="6e747-108">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="6e747-109">Считывает данные из объединенной сборки для указанного относительного виртуального адреса (RVA) в объединенной сборке.</span><span class="sxs-lookup"><span data-stu-id="6e747-109">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="6e747-110">Метод GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="6e747-110">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="6e747-111">Возвращает метаданные из объединенной сборки.</span><span class="sxs-lookup"><span data-stu-id="6e747-111">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="6e747-112">Метод GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="6e747-112">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="6e747-113">Получает начальный адрес метода и размер для указанного относительного виртуального адреса (RVA) в методе.</span><span class="sxs-lookup"><span data-stu-id="6e747-113">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="6e747-114">Метод GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="6e747-114">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="6e747-115">Получает символы поля экземпляра, которые соответствуют сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="6e747-115">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="6e747-116">Метод GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="6e747-116">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="6e747-117">Возвращает символьные записи для всех объединенных сборок.</span><span class="sxs-lookup"><span data-stu-id="6e747-117">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="6e747-118">Метод GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="6e747-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="6e747-119">Получает локальные символы метода с учетом относительного виртуального адреса (RVA) этого метода.</span><span class="sxs-lookup"><span data-stu-id="6e747-119">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="6e747-120">Метод GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="6e747-120">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="6e747-121">Получает символы параметров метода для указанного относительного виртуального адреса (RVA) этого метода.</span><span class="sxs-lookup"><span data-stu-id="6e747-121">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="6e747-122">Метод GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="6e747-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="6e747-123">Возвращает сведения о свойствах метода, такие как токен метаданных метода и сведения о его универсальных параметрах, для указанного относительного виртуального адреса (RVA) в этом методе.</span><span class="sxs-lookup"><span data-stu-id="6e747-123">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="6e747-124">Метод GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="6e747-124">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="6e747-125">Возвращает размер объекта для объекта на основе его сигнатуры TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="6e747-125">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="6e747-126">Метод GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="6e747-126">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="6e747-127">Получает символы статического поля, которые соответствуют сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="6e747-127">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="6e747-128">Метод GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="6e747-128">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="6e747-129">Возвращает сведения о свойствах типа, такие как число сигнатур его универсальных параметров, для указанного относительного виртуального адреса (RVA) в таблице VTable.</span><span class="sxs-lookup"><span data-stu-id="6e747-129">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e747-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="6e747-130">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e747-131">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6e747-131">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6e747-132">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6e747-132">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e747-133">Требования</span><span class="sxs-lookup"><span data-stu-id="6e747-133">Requirements</span></span>  

 <span data-ttu-id="6e747-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e747-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e747-135">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e747-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e747-136">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e747-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e747-137">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e747-137">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e747-138">См. также</span><span class="sxs-lookup"><span data-stu-id="6e747-138">See also</span></span>

- [<span data-ttu-id="6e747-139">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6e747-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6e747-140">Отладка</span><span class="sxs-lookup"><span data-stu-id="6e747-140">Debugging</span></span>](index.md)
