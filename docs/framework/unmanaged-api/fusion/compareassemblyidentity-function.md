---
description: Дополнительные сведения о функции Компареассемблидентити
title: Функция CompareAssemblyIdentity
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: aa55d1ea0b1968ec4e50106139e154e29e159ec7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761217"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="adaac-103">Функция CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="adaac-103">CompareAssemblyIdentity Function</span></span>

<span data-ttu-id="adaac-104">Сравнивает два идентификатора сборки, чтобы определить, являются ли они эквивалентными.</span><span class="sxs-lookup"><span data-stu-id="adaac-104">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adaac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="adaac-105">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="adaac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="adaac-106">Parameters</span></span>  

 `pwzAssemblyIdentity1`  
 <span data-ttu-id="adaac-107">окне Текстовое удостоверение первой сборки в сравнении.</span><span class="sxs-lookup"><span data-stu-id="adaac-107">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="adaac-108">окне Логический флаг, который указывает на определенное пользователем унификацию для `pwzAssemblyIdentity1` .</span><span class="sxs-lookup"><span data-stu-id="adaac-108">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="adaac-109">окне Текстовое удостоверение второй сборки в сравнении.</span><span class="sxs-lookup"><span data-stu-id="adaac-109">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="adaac-110">окне Логический флаг, который указывает на определенное пользователем унификацию для `pwzAssemblyIdentity2` .</span><span class="sxs-lookup"><span data-stu-id="adaac-110">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="adaac-111">заполняет Логический флаг, указывающий, эквивалентны ли две сборки.</span><span class="sxs-lookup"><span data-stu-id="adaac-111">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="adaac-112">заполняет Перечисление [ассембликомпарисонресулт](assemblycomparisonresult-enumeration.md) , содержащее подробные сведения о сравнении.</span><span class="sxs-lookup"><span data-stu-id="adaac-112">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adaac-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="adaac-113">Return Value</span></span>  

 <span data-ttu-id="adaac-114">`pfEquivalent` Возвращает логическое значение, указывающее, эквивалентны ли две сборки.</span><span class="sxs-lookup"><span data-stu-id="adaac-114">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="adaac-115">`pResult` Возвращает одно из `AssemblyComparisonResult` значений, чтобы получить более подробную причину для значения `pfEquivalent` .</span><span class="sxs-lookup"><span data-stu-id="adaac-115">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adaac-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="adaac-116">Remarks</span></span>  

 <span data-ttu-id="adaac-117">`CompareAssemblyIdentity` проверяет, `pwzAssemblyIdentity1` `pwzAssemblyIdentity2` эквивалентны ли и.</span><span class="sxs-lookup"><span data-stu-id="adaac-117">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="adaac-118">`pfEquivalent` задается в `true` одном или нескольких следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="adaac-118">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="adaac-119">Два удостоверения сборки эквивалентны.</span><span class="sxs-lookup"><span data-stu-id="adaac-119">The two assembly identities are equivalent.</span></span> <span data-ttu-id="adaac-120">Для строго именованных сборок эквивалентность требует идентичности имени сборки, версии, токена открытого ключа и языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="adaac-120">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="adaac-121">Для просто именованных сборок эквивалентность требует соответствия имени сборки и языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="adaac-121">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="adaac-122">Оба удостоверения сборки ссылаются на сборки, которые выполняются в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adaac-122">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="adaac-123">Это условие возвращает значение `true` , даже если номера версий сборки не совпадают.</span><span class="sxs-lookup"><span data-stu-id="adaac-123">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="adaac-124">Эти две сборки не являются управляемыми сборками, но `fUnified1` или имеют `fUnified2` значение `true` .</span><span class="sxs-lookup"><span data-stu-id="adaac-124">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="adaac-125">`fUnified`Флаг указывает, что все номера версий, вплоть до номера версии строго именованной сборки, считаются эквивалентными сборке со строгим именем.</span><span class="sxs-lookup"><span data-stu-id="adaac-125">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="adaac-126">Например, если значение `pwzAssemblyIndentity1` равно "MyAssembly, Version = 3.0.0.0, Culture = Neutral, PublicKeyToken =....", а значение `fUnified1` равно `true` , это означает, что все версии myAssembly от версии 0.0.0.0 до 3.0.0.0 должны рассматриваться как эквивалентные.</span><span class="sxs-lookup"><span data-stu-id="adaac-126">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="adaac-127">В этом случае, если `pwzAssemblyIndentity2` ссылается на ту же сборку, что `pwzAssemblyIndentity1` и, за исключением того, что имеет меньший номер версии, устанавливается `pfEquivalent` в значение `true` .</span><span class="sxs-lookup"><span data-stu-id="adaac-127">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="adaac-128">Если `pwzAssemblyIdentity2` ссылается на более высокий номер версии, `pfEquivalent` задается `true` только в том случае, если значение `fUnified2` равно `true` .</span><span class="sxs-lookup"><span data-stu-id="adaac-128">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="adaac-129">`pResult`Параметр содержит конкретные сведения о том, почему две сборки считаются эквивалентными или не эквивалентными.</span><span class="sxs-lookup"><span data-stu-id="adaac-129">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="adaac-130">Дополнительные сведения см. в разделе [перечисление ассембликомпарисонресулт](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="adaac-130">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adaac-131">Требования</span><span class="sxs-lookup"><span data-stu-id="adaac-131">Requirements</span></span>  

 <span data-ttu-id="adaac-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adaac-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adaac-133">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="adaac-133">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="adaac-134">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adaac-134">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adaac-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adaac-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adaac-136">См. также</span><span class="sxs-lookup"><span data-stu-id="adaac-136">See also</span></span>

- [<span data-ttu-id="adaac-137">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="adaac-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="adaac-138">Перечисление AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="adaac-138">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
