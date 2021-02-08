---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Жетмесодбиверсион'
title: Метод ISymUnmanagedReader::GetMethodByVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 6b2fa3ff3af91d59bb79029d039e5656610bebff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772072"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="13755-103">Метод ISymUnmanagedReader::GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="13755-103">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="13755-104">Возвращает метод чтения символов по заданному маркеру метода и номеру версии для редактирования и копирования.</span><span class="sxs-lookup"><span data-stu-id="13755-104">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="13755-105">Номера версий начинаются с 1 и увеличиваются каждый раз при изменении метода в результате операции редактирования и копирования.</span><span class="sxs-lookup"><span data-stu-id="13755-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13755-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13755-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13755-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="13755-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="13755-108">окне Токен метода.</span><span class="sxs-lookup"><span data-stu-id="13755-108">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="13755-109">окне Версия метода.</span><span class="sxs-lookup"><span data-stu-id="13755-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="13755-110">заполняет Указатель на возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="13755-110">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13755-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="13755-111">Return Value</span></span>  

 <span data-ttu-id="13755-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="13755-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13755-113">Требования</span><span class="sxs-lookup"><span data-stu-id="13755-113">Requirements</span></span>  

 <span data-ttu-id="13755-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="13755-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13755-115">См. также</span><span class="sxs-lookup"><span data-stu-id="13755-115">See also</span></span>

- [<span data-ttu-id="13755-116">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="13755-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
