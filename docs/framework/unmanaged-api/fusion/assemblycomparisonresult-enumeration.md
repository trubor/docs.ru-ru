---
description: Дополнительные сведения о перечислении Ассембликомпарисонресулт
title: Перечисление AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: 093cff830aa87d28ee86ecaeb6965887279a72d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761295"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="f016e-103">Перечисление AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="f016e-103">AssemblyComparisonResult Enumeration</span></span>

<span data-ttu-id="f016e-104">Указывает эквивалентность двух удостоверений сборки, как определено функцией [компареассемблидентити](compareassemblyidentity-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f016e-104">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f016e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f016e-105">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="f016e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f016e-106">Members</span></span>  
  
|<span data-ttu-id="f016e-107">Имя участника</span><span class="sxs-lookup"><span data-stu-id="f016e-107">Member name</span></span>|<span data-ttu-id="f016e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f016e-108">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="f016e-109">Указывает, что все поля сборки в совпадении сравнения.</span><span class="sxs-lookup"><span data-stu-id="f016e-109">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="f016e-110">Указывает, что сборки считаются эквивалентными на основе унификации номеров версий сборки среды CLR в версии платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f016e-110">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="f016e-111">Указывает частичное совпадение сборок на основе унификации версий сборки CLR в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f016e-111">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="f016e-112">Указывает частичное совпадение сборок.</span><span class="sxs-lookup"><span data-stu-id="f016e-112">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="f016e-113">Указывает частичное совпадение сборок на основе унификации устаревших номеров версий.</span><span class="sxs-lookup"><span data-stu-id="f016e-113">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="f016e-114">Указывает частичное совпадение с простыми именованными сборками.</span><span class="sxs-lookup"><span data-stu-id="f016e-114">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="f016e-115">Указывает, что сборки считаются эквивалентными на основе унификации версии CLR номеров версий в устаревших версиях платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f016e-115">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="f016e-116">Указывает соответствие между двумя простыми именованными сборками, Номера версий которых были пропущены.</span><span class="sxs-lookup"><span data-stu-id="f016e-116">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="f016e-117">Указывает, что между двумя сборками не произошло совпадений.</span><span class="sxs-lookup"><span data-stu-id="f016e-117">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="f016e-118">Указывает, что две сборки совпадают, за исключением номеров версий, которые соответствуют только частично.</span><span class="sxs-lookup"><span data-stu-id="f016e-118">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="f016e-119">Указывает, что две сборки совпадают, за исключением номеров версий, которые не совпадают.</span><span class="sxs-lookup"><span data-stu-id="f016e-119">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="f016e-120">Указывает, что причина неравенства неизвестна.</span><span class="sxs-lookup"><span data-stu-id="f016e-120">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f016e-121">Требования</span><span class="sxs-lookup"><span data-stu-id="f016e-121">Requirements</span></span>  

 <span data-ttu-id="f016e-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f016e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f016e-123">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f016e-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f016e-124">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f016e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f016e-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f016e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f016e-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f016e-126">See also</span></span>

- [<span data-ttu-id="f016e-127">Функция CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="f016e-127">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="f016e-128">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="f016e-128">Fusion Enumerations</span></span>](fusion-enumerations.md)
