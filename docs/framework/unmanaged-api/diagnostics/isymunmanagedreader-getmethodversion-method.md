---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: GetMethodVersion'
title: Метод ISymUnmanagedReader::GetMethodVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: 027f65f858aab3e4ad0bc0bfbffd91f6118b80b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764025"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="f6282-103">Метод ISymUnmanagedReader::GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="f6282-103">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="f6282-104">Возвращает версию метода.</span><span class="sxs-lookup"><span data-stu-id="f6282-104">Gets the method version.</span></span> <span data-ttu-id="f6282-105">Версия метода начинается с 1 и увеличивается каждый раз при повторной компиляции метода.</span><span class="sxs-lookup"><span data-stu-id="f6282-105">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="f6282-106">Перекомпиляция может произойти без изменения метода.</span><span class="sxs-lookup"><span data-stu-id="f6282-106">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6282-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6282-107">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6282-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="f6282-108">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="f6282-109">окне Метод, для которого необходимо получить версию.</span><span class="sxs-lookup"><span data-stu-id="f6282-109">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="f6282-110">заполняет Указатель на переменную, которая получает версию метода.</span><span class="sxs-lookup"><span data-stu-id="f6282-110">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6282-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f6282-111">Return Value</span></span>  

 <span data-ttu-id="f6282-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f6282-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6282-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f6282-113">Requirements</span></span>  

 <span data-ttu-id="f6282-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f6282-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6282-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f6282-115">See also</span></span>

- [<span data-ttu-id="f6282-116">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f6282-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
