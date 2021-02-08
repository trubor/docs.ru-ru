---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: Жетчекксумалгорисмид'
title: Метод ISymUnmanagedDocument::GetCheckSumAlgorithmId
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 835f56875a1adc3a3b6617a5a0b280f60f918236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772124"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="08214-103">Метод ISymUnmanagedDocument::GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="08214-103">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>

<span data-ttu-id="08214-104">Возвращает идентификатор алгоритма контрольной суммы или возвращает идентификатор GUID всех нулей, если контрольная сумма отсутствует.</span><span class="sxs-lookup"><span data-stu-id="08214-104">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08214-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08214-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08214-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="08214-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="08214-107">заполняет Указатель на переменную, которая получает идентификатор алгоритма контрольной суммы.</span><span class="sxs-lookup"><span data-stu-id="08214-107">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08214-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="08214-108">Return Value</span></span>  

 <span data-ttu-id="08214-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="08214-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08214-110">См. также</span><span class="sxs-lookup"><span data-stu-id="08214-110">See also</span></span>

- [<span data-ttu-id="08214-111">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="08214-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
