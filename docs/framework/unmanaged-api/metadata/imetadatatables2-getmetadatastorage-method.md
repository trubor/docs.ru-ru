---
description: 'Дополнительные сведения о методе: IMetaDataTables2:: Жетметадатастораже'
title: Метод IMetaDataTables2::GetMetaDataStorage
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: df6bbc69be05986dc6d4f143cec7ec09a2d78ee5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799256"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="a0171-103">Метод IMetaDataTables2::GetMetaDataStorage</span><span class="sxs-lookup"><span data-stu-id="a0171-103">IMetaDataTables2::GetMetaDataStorage Method</span></span>

<span data-ttu-id="a0171-104">Возвращает размер и содержимое метаданных, хранящихся в указанном разделе.</span><span class="sxs-lookup"><span data-stu-id="a0171-104">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0171-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a0171-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0171-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a0171-106">Parameters</span></span>  

 `ppvMd`  
 <span data-ttu-id="a0171-107">[вход, выход] Указатель на раздел метаданных.</span><span class="sxs-lookup"><span data-stu-id="a0171-107">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="a0171-108">заполняет Размер потока метаданных.</span><span class="sxs-lookup"><span data-stu-id="a0171-108">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0171-109">Требования</span><span class="sxs-lookup"><span data-stu-id="a0171-109">Requirements</span></span>  

 <span data-ttu-id="a0171-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0171-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0171-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a0171-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0171-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0171-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0171-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0171-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0171-114">См. также</span><span class="sxs-lookup"><span data-stu-id="a0171-114">See also</span></span>

- [<span data-ttu-id="a0171-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a0171-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="a0171-116">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a0171-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
