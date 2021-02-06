---
description: Дополнительные сведения о методе Ресолветипелиб
title: Метод ResolveTypeLib
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: ca7f94f630479d30bb9129497b38bcf04e759e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646287"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="d413c-103">Метод ResolveTypeLib</span><span class="sxs-lookup"><span data-stu-id="d413c-103">ResolveTypeLib Method</span></span>

<span data-ttu-id="d413c-104">Разрешает простое имя библиотеки типов, возвращая полный путь.</span><span class="sxs-lookup"><span data-stu-id="d413c-104">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d413c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d413c-105">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d413c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d413c-106">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="d413c-107">окне Значение типа [BSTR](/previous-versions/windows/desktop/automat/bstr) , содержащее простое имя библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="d413c-107">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="d413c-108">окне Идентификатор GUID, назначенный библиотеке типов в реестре.</span><span class="sxs-lookup"><span data-stu-id="d413c-108">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="d413c-109">окне ИДЕНТИФИКАТОР локализации библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="d413c-109">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="d413c-110">окне Основной номер версии библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="d413c-110">[in] The major version number of the type library.</span></span> <span data-ttu-id="d413c-111">Например, для версии *x. y* основной номер версии — *x*.</span><span class="sxs-lookup"><span data-stu-id="d413c-111">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="d413c-112">окне Дополнительный номер версии библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="d413c-112">[in] The minor version number of the type library.</span></span> <span data-ttu-id="d413c-113">Например, для версии *x. y* дополнительный номер версии — *y*.</span><span class="sxs-lookup"><span data-stu-id="d413c-113">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="d413c-114">окне Флаг [Сискинд](/windows/win32/api/oaidl/ne-oaidl-syskind) , определяющий операционную среду.</span><span class="sxs-lookup"><span data-stu-id="d413c-114">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="d413c-115">Распространенные значения: SYS_WIN32 и SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="d413c-115">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="d413c-116">заполняет Указатель на [BSTR](/previous-versions/windows/desktop/automat/bstr) , содержащий полный путь к библиотеке типов с именем в `bstrSimpleName` параметре.</span><span class="sxs-lookup"><span data-stu-id="d413c-116">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d413c-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="d413c-117">Remarks</span></span>  

 <span data-ttu-id="d413c-118">`ResolveTypeLib`Метод вызывается [функцией LoadTypeLibWithResolver](loadtypelibwithresolver-function.md) во время обработки [Tlbexp.exe (средство экспорта библиотеки типов)](../../tools/tlbexp-exe-type-library-exporter.md) .</span><span class="sxs-lookup"><span data-stu-id="d413c-118">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="d413c-119">Пользовательские реализации этого интерфейса должны возвращать [строку BSTR](/previous-versions/windows/desktop/automat/bstr) , содержащую полный путь к библиотеке типов с именем в `bstrSimpleName` параметре.</span><span class="sxs-lookup"><span data-stu-id="d413c-119">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d413c-120">Требования</span><span class="sxs-lookup"><span data-stu-id="d413c-120">Requirements</span></span>  

 <span data-ttu-id="d413c-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d413c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d413c-122">**Заголовок:** Тлбреф. idl, Тлбреф. h</span><span class="sxs-lookup"><span data-stu-id="d413c-122">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="d413c-123">**Библиотека:** Тлбреф. lib</span><span class="sxs-lookup"><span data-stu-id="d413c-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="d413c-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d413c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d413c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="d413c-125">See also</span></span>

- [<span data-ttu-id="d413c-126">Вспомогательные функции Tlbexp</span><span class="sxs-lookup"><span data-stu-id="d413c-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="d413c-127">лоадтипелибекс</span><span class="sxs-lookup"><span data-stu-id="d413c-127">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
