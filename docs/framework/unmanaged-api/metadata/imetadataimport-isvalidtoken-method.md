---
description: 'Дополнительные сведения: метод IMetaDataImport:: Исвалидтокен'
title: Метод IMetaDataImport::IsValidToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 68589496213c93f81cfbd0992f9b210e03d6f178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789064"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="2c3ca-103">Метод IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="2c3ca-103">IMetaDataImport::IsValidToken Method</span></span>

<span data-ttu-id="2c3ca-104">Возвращает значение, указывающее, содержится ли в заданном токене допустимая ссылка на объект кода.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-104">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3ca-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c3ca-105">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c3ca-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2c3ca-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="2c3ca-107">окне Токен, для которого проверяется допустимость ссылки.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-107">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c3ca-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2c3ca-108">Return Value</span></span>  

 <span data-ttu-id="2c3ca-109">`true` Если `tk` является допустимым токеном метаданных в текущей области.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-109">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="2c3ca-110">В противном случае — значение `false`.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-110">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3ca-111">Требования</span><span class="sxs-lookup"><span data-stu-id="2c3ca-111">Requirements</span></span>  

 <span data-ttu-id="2c3ca-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3ca-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2c3ca-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c3ca-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c3ca-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3ca-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3ca-116">См. также</span><span class="sxs-lookup"><span data-stu-id="2c3ca-116">See also</span></span>

- [<span data-ttu-id="2c3ca-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2c3ca-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2c3ca-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2c3ca-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
