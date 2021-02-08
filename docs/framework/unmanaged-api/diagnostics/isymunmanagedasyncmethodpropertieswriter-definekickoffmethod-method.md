---
description: 'Дополнительные сведения о методе: метод isymunmanagedasyncmethodpropertieswriter::D Ефинекиккоффмесод'
title: Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 7333823bce27eace4e9cb988ac31252743cca952
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790234"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="39db2-103">Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="39db2-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="39db2-104">Задает начальный метод, инициирующий асинхронную операцию.</span><span class="sxs-lookup"><span data-stu-id="39db2-104">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39db2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39db2-105">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39db2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="39db2-106">Parameters</span></span>  
  
|<span data-ttu-id="39db2-107">Параметр</span><span class="sxs-lookup"><span data-stu-id="39db2-107">Parameter</span></span>|<span data-ttu-id="39db2-108">Описание</span><span class="sxs-lookup"><span data-stu-id="39db2-108">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="39db2-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="39db2-109">Return Value</span></span>  

 <span data-ttu-id="39db2-110">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="39db2-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39db2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="39db2-111">Requirements</span></span>  

 <span data-ttu-id="39db2-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="39db2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39db2-113">См. также</span><span class="sxs-lookup"><span data-stu-id="39db2-113">See also</span></span>

- [<span data-ttu-id="39db2-114">Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="39db2-114">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
