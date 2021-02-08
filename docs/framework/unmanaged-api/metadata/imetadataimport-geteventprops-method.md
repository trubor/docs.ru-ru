---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetEventProps'
title: Метод IMetaDataImport::GetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 2680c48254ce7386a1a070667896aecd3bfac100
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789220"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="d4162-103">Метод IMetaDataImport::GetEventProps</span><span class="sxs-lookup"><span data-stu-id="d4162-103">IMetaDataImport::GetEventProps Method</span></span>

<span data-ttu-id="d4162-104">Возвращает сведения о метаданных для события, представленного указанным маркером события, включая объявляющий тип, методы добавления и удаления для делегатов, а также любые флаги и другие связанные данные.</span><span class="sxs-lookup"><span data-stu-id="d4162-104">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4162-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4162-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4162-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d4162-106">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="d4162-107">окне Токен метаданных события, представляющий событие, для которого необходимо получить метаданные.</span><span class="sxs-lookup"><span data-stu-id="d4162-107">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d4162-108">заполняет Указатель на маркер TypeDef, представляющий класс, объявляющий событие.</span><span class="sxs-lookup"><span data-stu-id="d4162-108">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="d4162-109">заполняет Имя события, на которое ссылается `ev` .</span><span class="sxs-lookup"><span data-stu-id="d4162-109">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="d4162-110">окне Запрошенная длина в расширенных символах `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="d4162-110">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="d4162-111">заполняет Возвращаемая длина в расширенных символах `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="d4162-111">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="d4162-112">заполняет Указатель на маркер метаданных TypeRef или TypeDef, представляющий <xref:System.Delegate> Тип события.</span><span class="sxs-lookup"><span data-stu-id="d4162-112">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="d4162-113">заполняет Указатель на маркер метаданных, представляющий метод, который добавляет обработчики для события.</span><span class="sxs-lookup"><span data-stu-id="d4162-113">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="d4162-114">заполняет Указатель на маркер метаданных, представляющий метод, который удаляет обработчики для события.</span><span class="sxs-lookup"><span data-stu-id="d4162-114">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="d4162-115">заполняет Указатель на маркер метаданных, представляющий метод, который вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="d4162-115">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="d4162-116">заполняет Массив указателей токенов на другие методы, связанные с событием.</span><span class="sxs-lookup"><span data-stu-id="d4162-116">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d4162-117">[in] Максимальный размер массива `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="d4162-117">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="d4162-118">заполняет Число токенов, возвращаемых в `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="d4162-118">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4162-119">Требования</span><span class="sxs-lookup"><span data-stu-id="d4162-119">Requirements</span></span>  

 <span data-ttu-id="d4162-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4162-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4162-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="d4162-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4162-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4162-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4162-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4162-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4162-124">См. также</span><span class="sxs-lookup"><span data-stu-id="d4162-124">See also</span></span>

- [<span data-ttu-id="d4162-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d4162-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d4162-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d4162-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
