---
description: 'Подробнее о: ISymUnmanagedDocument:: метод языка'
title: Метод ISymUnmanagedDocument::GetLanguage
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: f30636303d310ed91aa4229f52a3197a29190d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710313"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="dbc00-103">Метод ISymUnmanagedDocument::GetLanguage</span><span class="sxs-lookup"><span data-stu-id="dbc00-103">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="dbc00-104">Возвращает идентификатор языка этого документа.</span><span class="sxs-lookup"><span data-stu-id="dbc00-104">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc00-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbc00-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc00-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dbc00-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="dbc00-107">заполняет Указатель на переменную, которая получает идентификатор языка.</span><span class="sxs-lookup"><span data-stu-id="dbc00-107">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc00-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dbc00-108">Return Value</span></span>  

 <span data-ttu-id="dbc00-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="dbc00-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc00-110">См. также</span><span class="sxs-lookup"><span data-stu-id="dbc00-110">See also</span></span>

- [<span data-ttu-id="dbc00-111">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="dbc00-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
