---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: GetSaveSize'
title: Метод IMetaDataEmit::GetSaveSize
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 871e9f911eaaf1b1a7259466402e492d75aa7fb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783941"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="222c5-103">Метод IMetaDataEmit::GetSaveSize</span><span class="sxs-lookup"><span data-stu-id="222c5-103">IMetaDataEmit::GetSaveSize Method</span></span>

<span data-ttu-id="222c5-104">Возвращает приблизительный двоичный размер сборки и ее метаданных в текущей области.</span><span class="sxs-lookup"><span data-stu-id="222c5-104">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="222c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="222c5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="222c5-106">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="222c5-107">окне Значение перечисления [корсавесизе](corsavesize-enumeration.md) , указывающее, следует ли получить точный или приблизительный размер.</span><span class="sxs-lookup"><span data-stu-id="222c5-107">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="222c5-108">Допустимы только три значения: Кссаккурате, Ксскуикк и Кссдискардтрансиенткас:</span><span class="sxs-lookup"><span data-stu-id="222c5-108">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="222c5-109">Кссаккурате возвращает точный размер сохранения, но для его вычисления требуется больше времени.</span><span class="sxs-lookup"><span data-stu-id="222c5-109">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="222c5-110">Ксскуикк возвращает размер, дополненный для безопасности, но требует меньше времени для вычисления.</span><span class="sxs-lookup"><span data-stu-id="222c5-110">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="222c5-111">Кссдискардтрансиенткас сообщает `GetSaveSize` , что он может создавать неразрешенные настраиваемые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="222c5-111">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="222c5-112">заполняет Указатель на размер, необходимый для сохранения файла.</span><span class="sxs-lookup"><span data-stu-id="222c5-112">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="222c5-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="222c5-113">Remarks</span></span>  

 <span data-ttu-id="222c5-114">`GetSaveSize` Вычисляет пространство, необходимое в байтах, для сохранения сборки и всех ее метаданных в текущей области.</span><span class="sxs-lookup"><span data-stu-id="222c5-114">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="222c5-115">(Вызов метода [IMetaDataEmit:: саветостреам](imetadataemit-savetostream-method.md) приведет к порождению этого числа байтов.)</span><span class="sxs-lookup"><span data-stu-id="222c5-115">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="222c5-116">Если вызывающий объект реализует интерфейс [IMapToken](imaptoken-interface.md) (через [IMetaDataEmit:: сесандлер](imetadataemit-sethandler-method.md) или [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)), `GetSaveSize` выполняет два прохода по метаданным для оптимизации и сжатия.</span><span class="sxs-lookup"><span data-stu-id="222c5-116">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="222c5-117">В противном случае оптимизация не выполняется.</span><span class="sxs-lookup"><span data-stu-id="222c5-117">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="222c5-118">Если выполняется оптимизация, первый проход просто сортирует структуры метаданных для настройки производительности поисков во время поиска.</span><span class="sxs-lookup"><span data-stu-id="222c5-118">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="222c5-119">Этот шаг обычно приводит к перемещению записей, с побочным действием, что токены, сохраняемые средством для будущего использования, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="222c5-119">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="222c5-120">Однако метаданные не сообщают вызывающему объекту об изменениях токена до второго прохода.</span><span class="sxs-lookup"><span data-stu-id="222c5-120">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="222c5-121">Во втором прохождении выполняются различные оптимизации, предназначенные для уменьшения общего размера метаданных, например для оптимизации (раннего связывания) `mdTypeRef` и `mdMemberRef` токенов, когда ссылка указывает на тип или член, объявленный в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="222c5-121">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="222c5-122">На этом этапе выполняется еще один цикл сопоставления маркеров.</span><span class="sxs-lookup"><span data-stu-id="222c5-122">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="222c5-123">После этого обработчик метаданных уведомляет вызывающий объект через свой `IMapToken` интерфейс о любых измененных значениях токенов.</span><span class="sxs-lookup"><span data-stu-id="222c5-123">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="222c5-124">Требования</span><span class="sxs-lookup"><span data-stu-id="222c5-124">Requirements</span></span>  

 <span data-ttu-id="222c5-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="222c5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="222c5-126">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="222c5-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="222c5-127">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="222c5-127">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="222c5-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="222c5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222c5-129">См. также</span><span class="sxs-lookup"><span data-stu-id="222c5-129">See also</span></span>

- [<span data-ttu-id="222c5-130">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="222c5-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="222c5-131">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="222c5-131">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
