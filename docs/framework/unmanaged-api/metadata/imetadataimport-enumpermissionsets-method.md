---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумпермиссионсетс'
title: Метод IMetaDataImport::EnumPermissionSets
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: 7138cb2a89ecbea1afbf3e9fccfcac26e7e0fd7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688758"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="43ee3-103">Метод IMetaDataImport::EnumPermissionSets</span><span class="sxs-lookup"><span data-stu-id="43ee3-103">IMetaDataImport::EnumPermissionSets Method</span></span>

<span data-ttu-id="43ee3-104">Перечисляет разрешения для объектов в указанной области метаданных.</span><span class="sxs-lookup"><span data-stu-id="43ee3-104">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ee3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="43ee3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ee3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="43ee3-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="43ee3-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="43ee3-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="43ee3-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="43ee3-108">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="43ee3-109">окне Токен метаданных, ограничивающий область поиска, или значение NULL для поиска по самой широкой области.</span><span class="sxs-lookup"><span data-stu-id="43ee3-109">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="43ee3-110">окне Флаги, представляющие <xref:System.Security.Permissions.SecurityAction> значения, которые необходимо включить в `rPermission` , или ноль, чтобы вернуть все действия.</span><span class="sxs-lookup"><span data-stu-id="43ee3-110">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="43ee3-111">заполняет Массив, используемый для хранения маркеров разрешений.</span><span class="sxs-lookup"><span data-stu-id="43ee3-111">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="43ee3-112">[in] Максимальный размер массива `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="43ee3-112">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="43ee3-113">заполняет Число маркеров разрешений, возвращаемых в `rPermission` .</span><span class="sxs-lookup"><span data-stu-id="43ee3-113">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43ee3-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="43ee3-114">Return Value</span></span>  
  
|<span data-ttu-id="43ee3-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43ee3-115">HRESULT</span></span>|<span data-ttu-id="43ee3-116">Описание</span><span class="sxs-lookup"><span data-stu-id="43ee3-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="43ee3-117">`EnumPermissionSets` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="43ee3-117">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="43ee3-118">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="43ee3-118">There are no tokens to enumerate.</span></span> <span data-ttu-id="43ee3-119">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="43ee3-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43ee3-120">Требования</span><span class="sxs-lookup"><span data-stu-id="43ee3-120">Requirements</span></span>  

 <span data-ttu-id="43ee3-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ee3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ee3-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="43ee3-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43ee3-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43ee3-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43ee3-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ee3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ee3-125">См. также</span><span class="sxs-lookup"><span data-stu-id="43ee3-125">See also</span></span>

- [<span data-ttu-id="43ee3-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="43ee3-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="43ee3-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="43ee3-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
