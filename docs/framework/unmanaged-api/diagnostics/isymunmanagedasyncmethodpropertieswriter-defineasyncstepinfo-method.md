---
description: 'Дополнительные сведения о методе: метод isymunmanagedasyncmethodpropertieswriter::D Ефинеасинкстепинфо'
title: Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f95436b10041ae5bfd56ca080a9b8ce70748022c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790247"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="e9757-103">Метод ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="e9757-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="e9757-104">Определите группу асинхронных операций await в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="e9757-104">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="e9757-105">Каждое значение yield Offset соответствует инструкции Return, определяющей потенциальный доход.</span><span class="sxs-lookup"><span data-stu-id="e9757-105">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="e9757-106">Каждая `breakpointMethod` / `breakpointOffset` пара сообщает нам, где будет возобновлена асинхронная операция, которая может быть в другом методе.</span><span class="sxs-lookup"><span data-stu-id="e9757-106">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9757-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9757-107">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9757-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="e9757-108">Parameters</span></span>  
  
|<span data-ttu-id="e9757-109">Параметр</span><span class="sxs-lookup"><span data-stu-id="e9757-109">Parameter</span></span>|<span data-ttu-id="e9757-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e9757-110">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e9757-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e9757-111">Return Value</span></span>  

 <span data-ttu-id="e9757-112">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e9757-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9757-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e9757-113">Requirements</span></span>  

 <span data-ttu-id="e9757-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="e9757-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9757-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e9757-115">See also</span></span>

- [<span data-ttu-id="e9757-116">Интерфейс ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="e9757-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
