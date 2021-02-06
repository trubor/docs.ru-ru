---
description: Дополнительные сведения о перечислении Ассемблйоптионс
title: Перечисление AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: aba9ecb3176f533e2d53e2e45fef3d1dc4e55077
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638422"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="23de9-103">Перечисление AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="23de9-103">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="23de9-104">Перечисляет параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="23de9-104">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23de9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="23de9-105">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="23de9-106">Поля</span><span class="sxs-lookup"><span data-stu-id="23de9-106">Fields</span></span>  
  
|<span data-ttu-id="23de9-107">Поле</span><span class="sxs-lookup"><span data-stu-id="23de9-107">Field</span></span>|<span data-ttu-id="23de9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="23de9-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23de9-109">оптассемтитле</span><span class="sxs-lookup"><span data-stu-id="23de9-109">optAssemTitle</span></span>|<span data-ttu-id="23de9-110">Строка — представляет заголовок сборки.</span><span class="sxs-lookup"><span data-stu-id="23de9-110">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="23de9-111">оптассемдескриптион</span><span class="sxs-lookup"><span data-stu-id="23de9-111">optAssemDescription</span></span>|<span data-ttu-id="23de9-112">Строка — содержит описание сборки.</span><span class="sxs-lookup"><span data-stu-id="23de9-112">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="23de9-113">оптассемконфиг</span><span class="sxs-lookup"><span data-stu-id="23de9-113">optAssemConfig</span></span>|<span data-ttu-id="23de9-114">Строка — содержит конфигурацию сборки.</span><span class="sxs-lookup"><span data-stu-id="23de9-114">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="23de9-115">оптассемос</span><span class="sxs-lookup"><span data-stu-id="23de9-115">optAssemOS</span></span>|<span data-ttu-id="23de9-116">Строка в кодировке: "Двосплатформид. Двосмажорверсион. Двосминорверсион".</span><span class="sxs-lookup"><span data-stu-id="23de9-116">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="23de9-117">оптассемпроцессор</span><span class="sxs-lookup"><span data-stu-id="23de9-117">optAssemProcessor</span></span>|<span data-ttu-id="23de9-118">ULONG</span><span class="sxs-lookup"><span data-stu-id="23de9-118">ULONG</span></span>|  
|<span data-ttu-id="23de9-119">оптассемлокале</span><span class="sxs-lookup"><span data-stu-id="23de9-119">optAssemLocale</span></span>|<span data-ttu-id="23de9-120">Строка — содержит языковой стандарт сборки.</span><span class="sxs-lookup"><span data-stu-id="23de9-120">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="23de9-121">оптассемверсион</span><span class="sxs-lookup"><span data-stu-id="23de9-121">optAssemVersion</span></span>|<span data-ttu-id="23de9-122">Строка в кодировке: "основная. Дополнительная. сборка. Редакция".</span><span class="sxs-lookup"><span data-stu-id="23de9-122">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="23de9-123">оптассемкомпани</span><span class="sxs-lookup"><span data-stu-id="23de9-123">optAssemCompany</span></span>|<span data-ttu-id="23de9-124">Строка — содержит компанию.</span><span class="sxs-lookup"><span data-stu-id="23de9-124">String - Contains the company.</span></span>|  
|<span data-ttu-id="23de9-125">оптассемпродукт</span><span class="sxs-lookup"><span data-stu-id="23de9-125">optAssemProduct</span></span>|<span data-ttu-id="23de9-126">Строка — содержит имя продукта.</span><span class="sxs-lookup"><span data-stu-id="23de9-126">String - Contains the product name.</span></span>|  
|<span data-ttu-id="23de9-127">оптассемпродуктверсион</span><span class="sxs-lookup"><span data-stu-id="23de9-127">optAssemProductVersion</span></span>|<span data-ttu-id="23de9-128">Строка (также известная как Информатионалверсион).</span><span class="sxs-lookup"><span data-stu-id="23de9-128">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="23de9-129">оптассемкопиригхт</span><span class="sxs-lookup"><span data-stu-id="23de9-129">optAssemCopyright</span></span>|<span data-ttu-id="23de9-130">Строка — содержит сведения об авторских правах.</span><span class="sxs-lookup"><span data-stu-id="23de9-130">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="23de9-131">оптассемтрадемарк</span><span class="sxs-lookup"><span data-stu-id="23de9-131">optAssemTrademark</span></span>|<span data-ttu-id="23de9-132">Строка — содержит сведения о товарном знаке.</span><span class="sxs-lookup"><span data-stu-id="23de9-132">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="23de9-133">оптассемкэйфиле</span><span class="sxs-lookup"><span data-stu-id="23de9-133">optAssemKeyFile</span></span>|<span data-ttu-id="23de9-134">Строка (имя файла).</span><span class="sxs-lookup"><span data-stu-id="23de9-134">String (file name).</span></span>|  
|<span data-ttu-id="23de9-135">оптассемкэйнаме</span><span class="sxs-lookup"><span data-stu-id="23de9-135">optAssemKeyName</span></span>|<span data-ttu-id="23de9-136">Строка (имя ключа).</span><span class="sxs-lookup"><span data-stu-id="23de9-136">String (The key name).</span></span>|  
|<span data-ttu-id="23de9-137">оптассемалгид</span><span class="sxs-lookup"><span data-stu-id="23de9-137">optAssemAlgID</span></span>|<span data-ttu-id="23de9-138">ULONG</span><span class="sxs-lookup"><span data-stu-id="23de9-138">ULONG</span></span>|  
|<span data-ttu-id="23de9-139">оптассемфлагс</span><span class="sxs-lookup"><span data-stu-id="23de9-139">optAssemFlags</span></span>|<span data-ttu-id="23de9-140">ULONG</span><span class="sxs-lookup"><span data-stu-id="23de9-140">ULONG</span></span>|  
|<span data-ttu-id="23de9-141">оптассемхалфсигн</span><span class="sxs-lookup"><span data-stu-id="23de9-141">optAssemHalfSign</span></span>|<span data-ttu-id="23de9-142">Bool (также называется DelaySign).</span><span class="sxs-lookup"><span data-stu-id="23de9-142">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="23de9-143">оптассемфилеверсион</span><span class="sxs-lookup"><span data-stu-id="23de9-143">optAssemFileVersion</span></span>|<span data-ttu-id="23de9-144">Строка, закодированная как "основная. Дополнительная. сборка. Редакция"--то же, что и ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="23de9-144">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="23de9-145">оптассемсателлитевер</span><span class="sxs-lookup"><span data-stu-id="23de9-145">optAssemSatelliteVer</span></span>|<span data-ttu-id="23de9-146">Строка, закодированная как "основная. Дополнительная. сборка. Редакция".</span><span class="sxs-lookup"><span data-stu-id="23de9-146">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="23de9-147">оптластассемоптион</span><span class="sxs-lookup"><span data-stu-id="23de9-147">optLastAssemOption</span></span>|<span data-ttu-id="23de9-148">Счетчик числа элементов.</span><span class="sxs-lookup"><span data-stu-id="23de9-148">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23de9-149">Требования</span><span class="sxs-lookup"><span data-stu-id="23de9-149">Requirements</span></span>  

 <span data-ttu-id="23de9-150">**Заголовок:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="23de9-150">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="23de9-151">**Библиотека**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="23de9-151">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23de9-152">См. также</span><span class="sxs-lookup"><span data-stu-id="23de9-152">See also</span></span>

- [<span data-ttu-id="23de9-153">Al.exe (компоновщик сборок)</span><span class="sxs-lookup"><span data-stu-id="23de9-153">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
