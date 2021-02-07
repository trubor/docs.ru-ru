---
description: 'Дополнительные сведения о методе: ISymENCUnmanagedMethod:: GetLineFromOffset'
title: Метод ISymENCUnmanagedMethod::GetLineFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 18fe942b509340c89a4c3044e02bf8e9d952f91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737965"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="d872e-103">Метод ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="d872e-103">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="d872e-104">Возвращает сведения о строке, связанные со смещением.</span><span class="sxs-lookup"><span data-stu-id="d872e-104">Gets the line information associated with an offset.</span></span> <span data-ttu-id="d872e-105">Если параметр offset ( `dwOffset` ) не является точкой последовательности, этот метод получает сведения о строке, связанные с предыдущим смещением.</span><span class="sxs-lookup"><span data-stu-id="d872e-105">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d872e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d872e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d872e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d872e-107">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="d872e-108">окне Значение типа `ULONG32` , содержащее смещение.</span><span class="sxs-lookup"><span data-stu-id="d872e-108">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="d872e-109">заполняет Указатель на объект `ULONG32` , получающий строку.</span><span class="sxs-lookup"><span data-stu-id="d872e-109">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="d872e-110">заполняет Указатель на объект `ULONG32` , который получает столбец.</span><span class="sxs-lookup"><span data-stu-id="d872e-110">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="d872e-111">заполняет Указатель на объект `ULONG32` , который получает конечную строку.</span><span class="sxs-lookup"><span data-stu-id="d872e-111">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="d872e-112">заполняет Указатель на объект `ULONG32` , который получает конечный столбец.</span><span class="sxs-lookup"><span data-stu-id="d872e-112">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="d872e-113">заполняет Указатель на объект `ULONG32` , который получает связанную точку последовательности.</span><span class="sxs-lookup"><span data-stu-id="d872e-113">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d872e-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d872e-114">Return Value</span></span>  

 <span data-ttu-id="d872e-115">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="d872e-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d872e-116">Требования</span><span class="sxs-lookup"><span data-stu-id="d872e-116">Requirements</span></span>  

 <span data-ttu-id="d872e-117">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="d872e-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d872e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d872e-118">See also</span></span>

- [<span data-ttu-id="d872e-119">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="d872e-119">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
