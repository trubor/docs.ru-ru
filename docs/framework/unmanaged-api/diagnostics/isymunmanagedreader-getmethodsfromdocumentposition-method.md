---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Getmethodsfromdocumentposition-'
title: Метод ISymUnmanagedReader::GetMethodsFromDocumentPosition
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 033bdce2cd70e578ebd3be8a187d983a2c58b99d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764038"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="ebd71-103">Метод ISymUnmanagedReader::GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="ebd71-103">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>

<span data-ttu-id="ebd71-104">Возвращает массив методов, каждый из которых содержит точку останова в заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="ebd71-104">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd71-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ebd71-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd71-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebd71-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="ebd71-107">окне Указанный документ.</span><span class="sxs-lookup"><span data-stu-id="ebd71-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="ebd71-108">окне Строка указанного документа.</span><span class="sxs-lookup"><span data-stu-id="ebd71-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="ebd71-109">окне Столбец указанного документа.</span><span class="sxs-lookup"><span data-stu-id="ebd71-109">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="ebd71-110">[in] Размер массива `pRetVal`.</span><span class="sxs-lookup"><span data-stu-id="ebd71-110">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="ebd71-111">заполняет Указатель на переменную, которая получает количество элементов, возвращаемых в `pRetVal` массиве.</span><span class="sxs-lookup"><span data-stu-id="ebd71-111">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ebd71-112">заполняет Массив указателей, каждый из которых указывает на объект [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , представляющий метод, содержащий точку останова.</span><span class="sxs-lookup"><span data-stu-id="ebd71-112">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebd71-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ebd71-113">Return Value</span></span>  

 <span data-ttu-id="ebd71-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ebd71-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd71-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ebd71-115">Requirements</span></span>  

 <span data-ttu-id="ebd71-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="ebd71-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd71-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ebd71-117">See also</span></span>

- [<span data-ttu-id="ebd71-118">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ebd71-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
