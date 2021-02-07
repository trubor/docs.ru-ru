---
description: 'Дополнительные сведения о методе: IMetaDataDispenserEx:: onoption'
title: Метод IMetaDataDispenserEx::GetOption
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: cf52a251c3c0e0485558a150b727d58eeae81995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753553"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="bca71-103">Метод IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="bca71-103">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="bca71-104">Возвращает значение указанного параметра для текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="bca71-104">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="bca71-105">Параметр определяет, как обрабатываются вызовы к текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="bca71-105">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca71-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bca71-106">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca71-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="bca71-107">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="bca71-108">окне Указатель на идентификатор GUID, указывающий параметр, который необходимо получить.</span><span class="sxs-lookup"><span data-stu-id="bca71-108">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="bca71-109">Список поддерживаемых идентификаторов GUID см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="bca71-109">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bca71-110">заполняет Значение возвращаемого параметра.</span><span class="sxs-lookup"><span data-stu-id="bca71-110">[out] The value of the returned option.</span></span> <span data-ttu-id="bca71-111">Тип этого значения будет представлять собой вариант типа указанного параметра.</span><span class="sxs-lookup"><span data-stu-id="bca71-111">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca71-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="bca71-112">Remarks</span></span>  

 <span data-ttu-id="bca71-113">В следующем списке показаны идентификаторы GUID, которые поддерживаются для этого метода.</span><span class="sxs-lookup"><span data-stu-id="bca71-113">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="bca71-114">Описание см. в описании метода [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bca71-114">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="bca71-115">Если `optionId` не находится в этом списке, этот метод возвращает значение HRESULT `E_INVALIDARG` , указывающее на неверный параметр.</span><span class="sxs-lookup"><span data-stu-id="bca71-115">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="bca71-116">метадатачеккдупликатесфор</span><span class="sxs-lookup"><span data-stu-id="bca71-116">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="bca71-117">метадатарефтодефчекк</span><span class="sxs-lookup"><span data-stu-id="bca71-117">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="bca71-118">метадатанотификатионфортокенмовемент</span><span class="sxs-lookup"><span data-stu-id="bca71-118">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="bca71-119">метадатасетенк</span><span class="sxs-lookup"><span data-stu-id="bca71-119">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="bca71-120">метадатаеррорифемитаутофордер</span><span class="sxs-lookup"><span data-stu-id="bca71-120">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="bca71-121">метадатаженератетцеадаптерс</span><span class="sxs-lookup"><span data-stu-id="bca71-121">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="bca71-122">метадаталинкероптионс</span><span class="sxs-lookup"><span data-stu-id="bca71-122">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca71-123">Требования</span><span class="sxs-lookup"><span data-stu-id="bca71-123">Requirements</span></span>  

 <span data-ttu-id="bca71-124">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca71-124">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca71-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="bca71-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bca71-126">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bca71-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bca71-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca71-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca71-128">См. также</span><span class="sxs-lookup"><span data-stu-id="bca71-128">See also</span></span>

- [<span data-ttu-id="bca71-129">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="bca71-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="bca71-130">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="bca71-130">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
