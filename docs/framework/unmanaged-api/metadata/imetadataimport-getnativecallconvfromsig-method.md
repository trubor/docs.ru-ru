---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetNativeCallConvFromSig'
title: Метод IMetaDataImport::GetNativeCallConvFromSig
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: 2fb5c347098f860f9ad32eab20c8b5bd6278f838
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677578"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="20bde-103">Метод IMetaDataImport::GetNativeCallConvFromSig</span><span class="sxs-lookup"><span data-stu-id="20bde-103">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>

<span data-ttu-id="20bde-104">Возвращает собственное соглашение о вызовах для метода, представленного заданным указателем на подпись.</span><span class="sxs-lookup"><span data-stu-id="20bde-104">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bde-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20bde-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20bde-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="20bde-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="20bde-107">окне Указатель на сигнатуру метаданных метода, для которого возвращается соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="20bde-107">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="20bde-108">окне Размер в байтах для `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="20bde-108">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="20bde-109">заполняет Указатель на собственное соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="20bde-109">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bde-110">Требования</span><span class="sxs-lookup"><span data-stu-id="20bde-110">Requirements</span></span>  

 <span data-ttu-id="20bde-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20bde-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bde-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="20bde-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20bde-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20bde-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20bde-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bde-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bde-115">См. также</span><span class="sxs-lookup"><span data-stu-id="20bde-115">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="20bde-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="20bde-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="20bde-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="20bde-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
