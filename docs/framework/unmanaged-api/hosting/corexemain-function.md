---
description: Дополнительные сведения о функции _CorExeMain
title: Функция _CorExeMain
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: f94197598d01255c35712aa682f83ca9be1fb377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717138"
---
# <a name="_corexemain-function"></a><span data-ttu-id="4df2c-103">Функция _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="4df2c-103">_CorExeMain Function</span></span>

<span data-ttu-id="4df2c-104">Инициализирует среду CLR, находит управляемую точку входа в заголовке CLR исполняемой сборки и начинает выполнение.</span><span class="sxs-lookup"><span data-stu-id="4df2c-104">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df2c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4df2c-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4df2c-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="4df2c-106">Remarks</span></span>  

 <span data-ttu-id="4df2c-107">Эта функция вызывается загрузчиком в процессах, созданных из управляемых исполняемых сборок.</span><span class="sxs-lookup"><span data-stu-id="4df2c-107">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="4df2c-108">Для сборок DLL загрузчик вызывает функцию [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4df2c-108">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="4df2c-109">Загрузчик операционной системы вызывает этот метод независимо от точки входа, указанной в файле изображения.</span><span class="sxs-lookup"><span data-stu-id="4df2c-109">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="4df2c-110">В Windows 98, Windows ME, Windows NT и Windows 2000 `_CorExeMain` функция вызывается непрямо через исправление в загрузчике операционной системы.</span><span class="sxs-lookup"><span data-stu-id="4df2c-110">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="4df2c-111">Во всех остальных версиях Windows он вызывается непосредственно загрузчиком операционной системы.</span><span class="sxs-lookup"><span data-stu-id="4df2c-111">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="4df2c-112">Дополнительные сведения см. в подразделе "Примечания" статьи [_CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4df2c-112">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df2c-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4df2c-113">Requirements</span></span>  

 <span data-ttu-id="4df2c-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df2c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df2c-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4df2c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4df2c-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4df2c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4df2c-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df2c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df2c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4df2c-118">See also</span></span>

- [<span data-ttu-id="4df2c-119">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="4df2c-119">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
