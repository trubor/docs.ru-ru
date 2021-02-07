---
description: 'Дополнительные сведения о методе: IMetaDataDispenserEx:: Опенскопеонитипеинфо'
title: Метод IMetaDataDispenserEx::OpenScopeOnITypeInfo
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
ms.openlocfilehash: bc36bac9e7c63f56f442f1e25fd7a6a93f75924b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753527"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="a5bf8-103">Метод IMetaDataDispenserEx::OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="a5bf8-103">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="a5bf8-104">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-104">This method is not implemented.</span></span> <span data-ttu-id="a5bf8-105">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5bf8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5bf8-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5bf8-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a5bf8-107">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="a5bf8-108">окне Указатель на интерфейс [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) , предоставляющий сведения о типе, в котором следует открыть область.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-108">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="a5bf8-109">окне Флаги режима открытия.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-109">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="a5bf8-110">окне Требуемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-110">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="a5bf8-111">заполняет Указатель на указатель на возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="a5bf8-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5bf8-112">Требования</span><span class="sxs-lookup"><span data-stu-id="a5bf8-112">Requirements</span></span>  

 <span data-ttu-id="a5bf8-113">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5bf8-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5bf8-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a5bf8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5bf8-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5bf8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5bf8-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5bf8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5bf8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a5bf8-117">See also</span></span>

- [<span data-ttu-id="a5bf8-118">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="a5bf8-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="a5bf8-119">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="a5bf8-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
