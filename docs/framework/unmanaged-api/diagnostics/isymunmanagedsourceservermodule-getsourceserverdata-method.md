---
description: 'Дополнительные сведения о методе: ISymUnmanagedSourceServerModule:: Жетсаурцесервердата'
title: Метод ISymUnmanagedSourceServerModule::GetSourceServerData
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: cdba764534000273170ccd693a3fbc7b5df9c3c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763167"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="fa173-103">Метод ISymUnmanagedSourceServerModule::GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="fa173-103">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>

<span data-ttu-id="fa173-104">Возвращает данные исходного сервера для модуля.</span><span class="sxs-lookup"><span data-stu-id="fa173-104">Returns the source server data for the module.</span></span> <span data-ttu-id="fa173-105">Вызывающий объект должен освободить ресурсы с помощью `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="fa173-105">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa173-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa173-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa173-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="fa173-107">Parameters</span></span>  

 `pDataByteCount`  
 <span data-ttu-id="fa173-108">заполняет Указатель на объект `ULONG32` , который получает размер (в байтах) данных сервера-источника.</span><span class="sxs-lookup"><span data-stu-id="fa173-108">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="fa173-109">заполняет Указатель на возвращаемое `pDataByteCount` значение.</span><span class="sxs-lookup"><span data-stu-id="fa173-109">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa173-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fa173-110">Return Value</span></span>  

 <span data-ttu-id="fa173-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="fa173-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa173-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fa173-112">Requirements</span></span>  

 <span data-ttu-id="fa173-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="fa173-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa173-114">См. также</span><span class="sxs-lookup"><span data-stu-id="fa173-114">See also</span></span>

- [<span data-ttu-id="fa173-115">Интерфейс ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="fa173-115">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
