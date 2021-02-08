---
description: 'Дополнительные сведения о методе: IMetaDataTables2:: GetMetaDataStreamInfo'
title: Метод IMetaDataTables2::GetMetaDataStreamInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 323c31931cc97f18ff09df83c57153a3629d0a10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799252"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="c48bb-103">Метод IMetaDataTables2::GetMetaDataStreamInfo</span><span class="sxs-lookup"><span data-stu-id="c48bb-103">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>

<span data-ttu-id="c48bb-104">Возвращает имя, размер и содержимое потока метаданных по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="c48bb-104">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c48bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c48bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c48bb-106">Parameters</span></span>  

 `ix`  
 <span data-ttu-id="c48bb-107">окне Индекс запрошенного потока метаданных.</span><span class="sxs-lookup"><span data-stu-id="c48bb-107">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="c48bb-108">заполняет Указатель на имя потока.</span><span class="sxs-lookup"><span data-stu-id="c48bb-108">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c48bb-109">заполняет Указатель на поток метаданных.</span><span class="sxs-lookup"><span data-stu-id="c48bb-109">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="c48bb-110">заполняет Размер (в байтах) `ppv` .</span><span class="sxs-lookup"><span data-stu-id="c48bb-110">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48bb-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c48bb-111">Requirements</span></span>  

 <span data-ttu-id="c48bb-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c48bb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c48bb-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c48bb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c48bb-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c48bb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c48bb-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48bb-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c48bb-116">See also</span></span>

- [<span data-ttu-id="c48bb-117">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c48bb-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="c48bb-118">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c48bb-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
