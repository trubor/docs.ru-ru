---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинемесод'
title: Метод IMetaDataEmit::DefineMethod
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: b0ba2bb68f1d4387229767f6f2550d64b9008898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677969"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="6e5c0-103">Метод IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="6e5c0-103">IMetaDataEmit::DefineMethod Method</span></span>

<span data-ttu-id="6e5c0-104">Создает определение для метода или глобальной функции с указанной сигнатурой и возвращает маркер в это определение метода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-104">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5c0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6e5c0-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5c0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6e5c0-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="6e5c0-107">окне `mdTypedef` Маркер родительского класса или родительского интерфейса метода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-107">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="6e5c0-108">Задайте `td` значение `mdTokenNil` , если вы определяете глобальную функцию.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-108">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="6e5c0-109">окне Имя члена в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-109">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="6e5c0-110">окне Значение перечисления [кормесодаттр](cormethodattr-enumeration.md) , определяющее атрибуты метода или глобальной функции.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-110">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6e5c0-111">окне Сигнатура метода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-111">[in] The method signature.</span></span> <span data-ttu-id="6e5c0-112">Подпись сохраняется, как указано.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-112">The signature is persisted as supplied.</span></span> <span data-ttu-id="6e5c0-113">Если необходимо указать дополнительные сведения для всех параметров, используйте метод [IMetaDataEmit:: сетпарампропс](imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e5c0-113">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6e5c0-114">окне Число байтов в `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="6e5c0-114">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="6e5c0-115">окне Адрес кода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-115">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="6e5c0-116">окне Значение перечисления [кормесодимпл](cormethodimpl-enumeration.md) , указывающее функции реализации метода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-116">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="6e5c0-117">заполняет Токен элемента.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-117">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e5c0-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="6e5c0-118">Remarks</span></span>  

 <span data-ttu-id="6e5c0-119">API метаданных гарантирует сохранение методов в том же порядке, в котором вызывающий объект создает их для данного включающего класса или интерфейса, указанного в `td` параметре.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-119">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="6e5c0-120">Дополнительные сведения об использовании `DefineMethod` и определенных параметрах параметров приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-120">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="6e5c0-121">Слоты в таблице V-Table</span><span class="sxs-lookup"><span data-stu-id="6e5c0-121">Slots in the V-table</span></span>  

 <span data-ttu-id="6e5c0-122">Среда выполнения использует определения методов для настройки слотов v-table.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-122">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="6e5c0-123">В случае, когда необходимо пропустить один или несколько слотов, например для сохранения четности с помощью макета COM-интерфейса, будет определен фиктивный метод, который занимает область или слоты в таблице v-table. Присвойте свойству `dwMethodFlags` `mdRTSpecialName` значение перечисления [кормесодаттр](cormethodattr-enumeration.md) и укажите имя:</span><span class="sxs-lookup"><span data-stu-id="6e5c0-123">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="6e5c0-124">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="6e5c0-124">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="6e5c0-125">где *SequenceNumber* — порядковый номер метода, а *каунтофслотс* — число слотов для пропуска в таблице v-table.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-125">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="6e5c0-126">Если *каунтофслотс* опущен, то предполагается значение 1.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-126">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="6e5c0-127">Эти фиктивные методы не могут быть вызываемыми из управляемого или неуправляемого кода и любая попытка их вызова из управляемого или неуправляемого кода создает исключение.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-127">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="6e5c0-128">Их единственная задача состоит в том, чтобы освободить место в таблице v-table, которую среда выполнения создает для интеграции COM.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-128">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="6e5c0-129">Дублирующиеся методы</span><span class="sxs-lookup"><span data-stu-id="6e5c0-129">Duplicate Methods</span></span>  

 <span data-ttu-id="6e5c0-130">Не следует определять дублирующиеся методы.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-130">You should not define duplicate methods.</span></span> <span data-ttu-id="6e5c0-131">Это значит, что не следует вызывать `DefineMethod` с помощью повторяющегося набора значений в `td` `wzName` `pvSig` параметрах, и.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-131">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="6e5c0-132">(Эти три параметра вместе уникально определяют метод.)</span><span class="sxs-lookup"><span data-stu-id="6e5c0-132">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="6e5c0-133">Однако можно использовать повторяющееся тройное значение, если для одного из определений методов задается `mdPrivateScope` бит в `dwMethodFlags` параметре.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-133">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="6e5c0-134">( `mdPrivateScope` Бит означает, что компилятор не будет создавать ссылку на это определение метода.)</span><span class="sxs-lookup"><span data-stu-id="6e5c0-134">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="6e5c0-135">Сведения о реализации метода</span><span class="sxs-lookup"><span data-stu-id="6e5c0-135">Method Implementation Information</span></span>  

 <span data-ttu-id="6e5c0-136">Сведения о реализации метода часто неизвестны во время объявления метода.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-136">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="6e5c0-137">Поэтому при вызове не нужно передавать значения в `ulCodeRVA` `dwImplFlags` параметрах и `DefineMethod` .</span><span class="sxs-lookup"><span data-stu-id="6e5c0-137">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="6e5c0-138">Значения можно указать позже с помощью [IMetaDataEmit:: сетмесодимплфлагс](imetadataemit-setmethodimplflags-method.md) или [IMetaDataEmit:: SetRVA](imetadataemit-setrva-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e5c0-138">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="6e5c0-139">В некоторых ситуациях, например при вызове платформы (PInvoke) или в сценариях COM-взаимодействия, тело метода не будет передано и `ulCodeRVA` должно быть установлено в ноль.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-139">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="6e5c0-140">В таких ситуациях метод не должен помечаться как абстрактный, поскольку среда выполнения обнаружит реализацию.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-140">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="6e5c0-141">Определение метода для PInvoke</span><span class="sxs-lookup"><span data-stu-id="6e5c0-141">Defining a Method for PInvoke</span></span>  

 <span data-ttu-id="6e5c0-142">Для вызова каждой неуправляемой функции через PInvoke необходимо определить управляемый метод, представляющий целевую неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-142">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="6e5c0-143">Чтобы определить управляемый метод, используйте `DefineMethod` с некоторыми параметрами, заданными определенными значениями, в зависимости от способа использования PInvoke:</span><span class="sxs-lookup"><span data-stu-id="6e5c0-143">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="6e5c0-144">True PInvoke — включает вызов внешнего неуправляемого метода, который находится в неуправляемой библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-144">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="6e5c0-145">Локальный PInvoke — включает вызов собственного неуправляемого метода, внедренного в текущий управляемый модуль.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-145">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="6e5c0-146">Параметры параметров приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-146">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="6e5c0-147">Параметр</span><span class="sxs-lookup"><span data-stu-id="6e5c0-147">Parameter</span></span>|<span data-ttu-id="6e5c0-148">Значения для истинного PInvoke</span><span class="sxs-lookup"><span data-stu-id="6e5c0-148">Values for true PInvoke</span></span>|<span data-ttu-id="6e5c0-149">Значения для локального вызова PInvoke</span><span class="sxs-lookup"><span data-stu-id="6e5c0-149">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="6e5c0-150">Set `mdStatic` ; clear `mdSynchronized` и `mdAbstract` .</span><span class="sxs-lookup"><span data-stu-id="6e5c0-150">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="6e5c0-151">Допустимая сигнатура метода общеязыковой среды выполнения (CLR) с параметрами, которые являются допустимыми управляемыми типами.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-151">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="6e5c0-152">Допустимая сигнатура метода CLR с параметрами, которые являются допустимыми управляемыми типами.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-152">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="6e5c0-153">0</span><span class="sxs-lookup"><span data-stu-id="6e5c0-153">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="6e5c0-154">Задайте значения для `miCil` и `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-154">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="6e5c0-155">Задайте значения для `miNative` и `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="6e5c0-155">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e5c0-156">Требования</span><span class="sxs-lookup"><span data-stu-id="6e5c0-156">Requirements</span></span>  

 <span data-ttu-id="6e5c0-157">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e5c0-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5c0-158">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6e5c0-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e5c0-159">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e5c0-159">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5c0-160">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5c0-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5c0-161">См. также</span><span class="sxs-lookup"><span data-stu-id="6e5c0-161">See also</span></span>

- [<span data-ttu-id="6e5c0-162">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6e5c0-162">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6e5c0-163">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6e5c0-163">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
