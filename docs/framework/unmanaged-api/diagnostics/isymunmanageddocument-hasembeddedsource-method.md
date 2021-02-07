---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: Хасембеддедсаурце'
title: Метод ISymUnmanagedDocument::HasEmbeddedSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: fcab83fea65d9a9e483bff9d2d75714c233718eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710131"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="969f9-103">Метод ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="969f9-103">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>

<span data-ttu-id="969f9-104">Возвращает `true` , если документ имеет исходный код, внедренный в отладочные символы; в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="969f9-104">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969f9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="969f9-105">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="969f9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="969f9-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="969f9-107">заполняет Указатель на переменную, которая указывает, имеет ли документ исходный код, внедренный в отладочные символы.</span><span class="sxs-lookup"><span data-stu-id="969f9-107">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="969f9-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="969f9-108">Return Value</span></span>  

 <span data-ttu-id="969f9-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="969f9-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969f9-110">См. также</span><span class="sxs-lookup"><span data-stu-id="969f9-110">See also</span></span>

- [<span data-ttu-id="969f9-111">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="969f9-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
