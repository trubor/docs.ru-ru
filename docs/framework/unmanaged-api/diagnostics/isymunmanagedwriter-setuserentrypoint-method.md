---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Сетусерентрипоинт'
title: Метод ISymUnmanagedWriter::SetUserEntryPoint
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: a01d23a0462fabd7a2fc259722dcdf2a1c8e0a4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761984"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="5d67e-103">Метод ISymUnmanagedWriter::SetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="5d67e-103">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>

<span data-ttu-id="5d67e-104">Задает определяемый пользователем метод, являющийся точкой входа для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="5d67e-104">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="5d67e-105">Например, эта точка входа может быть основным методом пользователя вместо заглушек, созданной компилятором до Main.</span><span class="sxs-lookup"><span data-stu-id="5d67e-105">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d67e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d67e-106">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d67e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="5d67e-107">Parameters</span></span>  

 `entryMethod`  
 <span data-ttu-id="5d67e-108">окне Токен метаданных для метода, который является точкой входа пользователя.</span><span class="sxs-lookup"><span data-stu-id="5d67e-108">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d67e-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5d67e-109">Return Value</span></span>  

 <span data-ttu-id="5d67e-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="5d67e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d67e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5d67e-111">Requirements</span></span>  

 <span data-ttu-id="5d67e-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="5d67e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d67e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5d67e-113">See also</span></span>

- [<span data-ttu-id="5d67e-114">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="5d67e-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
