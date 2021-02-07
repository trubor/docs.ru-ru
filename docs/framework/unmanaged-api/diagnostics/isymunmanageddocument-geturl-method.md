---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: GetURL'
title: Метод ISymUnmanagedDocument::GetURL
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: b39b36054d80f9ad2f9dd076e2055ccbc6526973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710196"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="ecd0b-103">Метод ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="ecd0b-103">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="ecd0b-104">Возвращает универсальный указатель ресурса (URL) для этого документа.</span><span class="sxs-lookup"><span data-stu-id="ecd0b-104">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd0b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ecd0b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecd0b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ecd0b-106">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="ecd0b-107">окне Размер буфера (в символах) `szURL` .</span><span class="sxs-lookup"><span data-stu-id="ecd0b-107">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="ecd0b-108">заполняет Указатель на переменную, которая получает размер URL-адреса, включая завершение, равное NULL.</span><span class="sxs-lookup"><span data-stu-id="ecd0b-108">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="ecd0b-109">заполняет Буфер, содержащий URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="ecd0b-109">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecd0b-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ecd0b-110">Return Value</span></span>  

 <span data-ttu-id="ecd0b-111">S_OK, если метод выполнен. в противном случае — код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ecd0b-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd0b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="ecd0b-112">See also</span></span>

- [<span data-ttu-id="ecd0b-113">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="ecd0b-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
