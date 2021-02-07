---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader2:: Жетмесодбиверсионпреремап'
title: Метод ISymUnmanagedReader2::GetMethodByVersionPreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b827821f529b9917c6bbb3452f0c3fe3283f1ee9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763726"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="e0bb9-103">Метод ISymUnmanagedReader2::GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="e0bb9-103">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>

<span data-ttu-id="e0bb9-104">Возвращает метод чтения символов по заданному маркеру метода и номеру версии "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="e0bb9-104">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="e0bb9-105">Номера версий начинаются с 1 и увеличиваются каждый раз при изменении метода в результате операции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="e0bb9-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bb9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0bb9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0bb9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e0bb9-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="e0bb9-108">окне Токен метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-108">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="e0bb9-109">окне Версия метода.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e0bb9-110">заполняет Указатель на возвращаемый интерфейс [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e0bb9-110">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0bb9-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e0bb9-111">Return Value</span></span>  

 <span data-ttu-id="e0bb9-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bb9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e0bb9-113">Requirements</span></span>  

 <span data-ttu-id="e0bb9-114">**Заголовок:** Корсим. idl.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-114">**Header:** CorSym.idl.</span></span> <span data-ttu-id="e0bb9-115">Корсим. h</span><span class="sxs-lookup"><span data-stu-id="e0bb9-115">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bb9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e0bb9-116">See also</span></span>

- [<span data-ttu-id="e0bb9-117">Интерфейс ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="e0bb9-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
