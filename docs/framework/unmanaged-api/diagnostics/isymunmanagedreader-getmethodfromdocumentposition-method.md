---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Жетмесодфромдокументпоситион'
title: Метод ISymUnmanagedReader::GetMethodFromDocumentPosition
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 1289b02f8ea8440dcd1b308b6c91a46a213cabb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764090"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="0261e-103">Метод ISymUnmanagedReader::GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="0261e-103">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>

<span data-ttu-id="0261e-104">Возвращает метод, содержащий точку останова в заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="0261e-104">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0261e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0261e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0261e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0261e-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="0261e-107">окне Указанный документ.</span><span class="sxs-lookup"><span data-stu-id="0261e-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="0261e-108">окне Строка указанного документа.</span><span class="sxs-lookup"><span data-stu-id="0261e-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="0261e-109">окне Столбец указанного документа.</span><span class="sxs-lookup"><span data-stu-id="0261e-109">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0261e-110">заполняет Указатель на адрес объекта [интерфейса ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , который представляет метод, содержащий точку останова.</span><span class="sxs-lookup"><span data-stu-id="0261e-110">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0261e-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0261e-111">Return Value</span></span>  

 <span data-ttu-id="0261e-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="0261e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0261e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="0261e-113">Requirements</span></span>  

 <span data-ttu-id="0261e-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0261e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0261e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0261e-115">See also</span></span>

- [<span data-ttu-id="0261e-116">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="0261e-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
