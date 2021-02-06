---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетфиелдрва'
title: Метод IMetaDataEmit::SetFieldRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 5d78880b892dc948337aa1ec1a471a5d380f1e2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657935"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="b7a07-103">Метод IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="b7a07-103">IMetaDataEmit::SetFieldRVA Method</span></span>

<span data-ttu-id="b7a07-104">Задает значение глобальной переменной для относительного виртуального адреса поля, на которое ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="b7a07-104">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a07-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7a07-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7a07-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7a07-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="b7a07-107">окне Токен для целевого поля.</span><span class="sxs-lookup"><span data-stu-id="b7a07-107">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b7a07-108">окне Адрес кода или области данных.</span><span class="sxs-lookup"><span data-stu-id="b7a07-108">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a07-109">Требования</span><span class="sxs-lookup"><span data-stu-id="b7a07-109">Requirements</span></span>  

 <span data-ttu-id="b7a07-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7a07-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a07-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b7a07-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7a07-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7a07-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7a07-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a07-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a07-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b7a07-114">See also</span></span>

- [<span data-ttu-id="b7a07-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b7a07-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b7a07-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b7a07-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
