---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedReader2'
title: Интерфейс ISymUnmanagedReader2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 2e6d994a3252b7fb09b2915266e3142255878a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763622"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="666e4-103">Интерфейс ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="666e4-103">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="666e4-104">Представляет средство чтения символов, которое предоставляет доступ к документам, методам и переменным в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="666e4-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="666e4-105">Этот интерфейс расширяет интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="666e4-105">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="666e4-106">Методы</span><span class="sxs-lookup"><span data-stu-id="666e4-106">Methods</span></span>  
  
|<span data-ttu-id="666e4-107">Метод</span><span class="sxs-lookup"><span data-stu-id="666e4-107">Method</span></span>|<span data-ttu-id="666e4-108">Описание</span><span class="sxs-lookup"><span data-stu-id="666e4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="666e4-109">Метод GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="666e4-109">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="666e4-110">Получение метода чтения символов по заданному маркеру метода и номеру версии "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="666e4-110">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="666e4-111">Метод GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="666e4-111">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="666e4-112">Возвращает каждый метод, имеющий сведения о строке в указанном документе.</span><span class="sxs-lookup"><span data-stu-id="666e4-112">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="666e4-113">Метод GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="666e4-113">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="666e4-114">Возвращает настраиваемый атрибут на основе его имени.</span><span class="sxs-lookup"><span data-stu-id="666e4-114">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="666e4-115">Требования</span><span class="sxs-lookup"><span data-stu-id="666e4-115">Requirements</span></span>  

 <span data-ttu-id="666e4-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="666e4-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666e4-117">См. также</span><span class="sxs-lookup"><span data-stu-id="666e4-117">See also</span></span>

- [<span data-ttu-id="666e4-118">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="666e4-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="666e4-119">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="666e4-119">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
