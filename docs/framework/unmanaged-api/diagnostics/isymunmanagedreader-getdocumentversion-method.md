---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: GetDocumentVersion'
title: Метод ISymUnmanagedReader::GetDocumentVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: e6877a10f0c285186330b320c9b614939f4d9e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800205"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="5153a-103">Метод ISymUnmanagedReader::GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="5153a-103">ISymUnmanagedReader::GetDocumentVersion Method</span></span>

<span data-ttu-id="5153a-104">Возвращает указанную версию указанного документа.</span><span class="sxs-lookup"><span data-stu-id="5153a-104">Gets the specified version of the specified document.</span></span> <span data-ttu-id="5153a-105">Версия документа начинается с 1 и увеличивается каждый раз при обновлении документа с помощью метода [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5153a-105">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="5153a-106">Если `pbCurrent` параметр имеет значение `true` , это последняя версия документа.</span><span class="sxs-lookup"><span data-stu-id="5153a-106">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5153a-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5153a-107">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5153a-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="5153a-108">Parameters</span></span>  

 `pDoc`  
 <span data-ttu-id="5153a-109">окне Указанный документ.</span><span class="sxs-lookup"><span data-stu-id="5153a-109">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="5153a-110">заполняет Указатель на переменную, которая получает версию указанного документа.</span><span class="sxs-lookup"><span data-stu-id="5153a-110">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="5153a-111">заполняет Указатель на переменную, которая получает, `true` если это последняя версия документа, или `false` если это не последняя версия.</span><span class="sxs-lookup"><span data-stu-id="5153a-111">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5153a-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5153a-112">Return Value</span></span>  

 <span data-ttu-id="5153a-113">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="5153a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5153a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5153a-114">Requirements</span></span>  

 <span data-ttu-id="5153a-115">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="5153a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5153a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5153a-116">See also</span></span>

- [<span data-ttu-id="5153a-117">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="5153a-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
