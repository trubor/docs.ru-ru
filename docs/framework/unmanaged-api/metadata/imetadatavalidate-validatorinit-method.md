---
description: 'Дополнительные сведения о методе: IMetaDataValidate:: ValidatorInit'
title: Метод IMetaDataValidate::ValidatorInit
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 99435eeab542e9cb3bb679ad146b546ce51c8df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799191"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="8d8fc-103">Метод IMetaDataValidate::ValidatorInit</span><span class="sxs-lookup"><span data-stu-id="8d8fc-103">IMetaDataValidate::ValidatorInit Method</span></span>

<span data-ttu-id="8d8fc-104">Устанавливает флаг, который указывает тип модуля в текущей области метаданных, и регистрирует указанный метод обратного вызова для ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="8d8fc-104">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d8fc-105">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d8fc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d8fc-106">Parameters</span></span>  

 `dwModule`  
 <span data-ttu-id="8d8fc-107">окне Значение перечисления [корвалидатормодулетипе](corvalidatormoduletype-enumeration.md) , указывающее тип модуля в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="8d8fc-107">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="8d8fc-108">окне Указатель на экземпляр [IUnknown](/cpp/atl/iunknown) , который служит функцией обратного вызова функции для ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="8d8fc-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d8fc-109">Требования</span><span class="sxs-lookup"><span data-stu-id="8d8fc-109">Requirements</span></span>  

 <span data-ttu-id="8d8fc-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d8fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d8fc-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8d8fc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d8fc-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d8fc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d8fc-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8fc-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8d8fc-114">See also</span></span>

- [<span data-ttu-id="8d8fc-115">Интерфейс IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="8d8fc-115">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
