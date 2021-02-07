---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: Жетлангуажевендор'
title: Метод ISymUnmanagedDocument::GetLanguageVendor
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
ms.openlocfilehash: 247c6c24f57211b3b46ad773d8e77d7e0f16fd01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710248"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="2437a-103">Метод ISymUnmanagedDocument::GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="2437a-103">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>

<span data-ttu-id="2437a-104">Получает поставщика языка этого документа.</span><span class="sxs-lookup"><span data-stu-id="2437a-104">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2437a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2437a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2437a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2437a-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="2437a-107">заполняет Указатель на переменную, которая получает поставщик языка.</span><span class="sxs-lookup"><span data-stu-id="2437a-107">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2437a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2437a-108">Return Value</span></span>  

 <span data-ttu-id="2437a-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="2437a-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2437a-110">См. также</span><span class="sxs-lookup"><span data-stu-id="2437a-110">See also</span></span>

- [<span data-ttu-id="2437a-111">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="2437a-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
