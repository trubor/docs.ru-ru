---
description: Дополнительные сведения о функции Жеттипелибинфо
title: Функция GetTypeLibInfo
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: 61a830f3ce81345634da377f6fc815a307700e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794472"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="92408-103">Функция GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="92408-103">GetTypeLibInfo Function</span></span>

<span data-ttu-id="92408-104">Возвращает сведения о указанной библиотеке типов, изучая ее структуру [тлибаттр](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="92408-104">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92408-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92408-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92408-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92408-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="92408-107">окне Имя файла библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-107">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="92408-108">заполняет Идентификатор GUID библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-108">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="92408-109">заполняет ИДЕНТИФИКАТОР локализации библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-109">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="92408-110">заполняет Флаг [Сискинд](/windows/win32/api/oaidl/ne-oaidl-syskind) , определяющий целевую операционную систему для библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-110">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="92408-111">Распространенные значения: SYS_WIN32 и SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="92408-111">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="92408-112">заполняет Основной номер версии библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-112">[out] The major version number of the type library.</span></span> <span data-ttu-id="92408-113">Например, для версии *x. y* основной номер версии — *x*.</span><span class="sxs-lookup"><span data-stu-id="92408-113">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="92408-114">заполняет Дополнительный номер версии библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="92408-114">[out] The minor version number of the type library.</span></span> <span data-ttu-id="92408-115">Например, для версии *x. y* дополнительный номер версии — *y*.</span><span class="sxs-lookup"><span data-stu-id="92408-115">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92408-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="92408-116">Remarks</span></span>  

 <span data-ttu-id="92408-117">`GetTypeLibInfo`Функция вызывается [Tlbexp.exe (программа экспорта библиотек типов)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="92408-117">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="92408-118">Это средство создает библиотеку типов, описывающую типы в сборке среды CLR.</span><span class="sxs-lookup"><span data-stu-id="92408-118">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="92408-119">Если какой-либо из параметров имеет значение null, функция возвращает объект `HRESULT` `E_POINTER` .</span><span class="sxs-lookup"><span data-stu-id="92408-119">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="92408-120">В противном случае возвращается значение `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="92408-120">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92408-121">Требования</span><span class="sxs-lookup"><span data-stu-id="92408-121">Requirements</span></span>  

 <span data-ttu-id="92408-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92408-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92408-123">**Заголовок:** Тлбреф. h</span><span class="sxs-lookup"><span data-stu-id="92408-123">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="92408-124">**Библиотека:** Тлбреф. lib</span><span class="sxs-lookup"><span data-stu-id="92408-124">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="92408-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92408-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92408-126">См. также</span><span class="sxs-lookup"><span data-stu-id="92408-126">See also</span></span>

- [<span data-ttu-id="92408-127">Вспомогательные функции Tlbexp</span><span class="sxs-lookup"><span data-stu-id="92408-127">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="92408-128">Функция Лоадтипелибекс</span><span class="sxs-lookup"><span data-stu-id="92408-128">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
