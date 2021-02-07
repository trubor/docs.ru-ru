---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Initialize'
title: Метод ISymUnmanagedReader::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: cf7f5df3efed7823fc36bd6c9fc56e0c49d17443
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763882"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="0a983-103">Метод ISymUnmanagedReader::Initialize</span><span class="sxs-lookup"><span data-stu-id="0a983-103">ISymUnmanagedReader::Initialize Method</span></span>

<span data-ttu-id="0a983-104">Инициализирует средство чтения символов с помощью интерфейса средства импорта метаданных, с которым будет связан этот модуль чтения, вместе с именем файла модуля.</span><span class="sxs-lookup"><span data-stu-id="0a983-104">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a983-105">Этот метод может быть вызван только один раз и должен вызываться до любых других методов чтения.</span><span class="sxs-lookup"><span data-stu-id="0a983-105">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a983-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a983-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a983-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0a983-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="0a983-108">окне Интерфейс средства импорта метаданных, с которым будет связан этот модуль чтения.</span><span class="sxs-lookup"><span data-stu-id="0a983-108">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="0a983-109">окне Имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="0a983-109">[in] The file name of the module.</span></span> <span data-ttu-id="0a983-110">Вместо этого можно использовать `pIStream` параметр.</span><span class="sxs-lookup"><span data-stu-id="0a983-110">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="0a983-111">окне Путь для поиска.</span><span class="sxs-lookup"><span data-stu-id="0a983-111">[in] The path to search.</span></span> <span data-ttu-id="0a983-112">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="0a983-112">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="0a983-113">окне Файловый поток, используемый в качестве альтернативы параметру filename.</span><span class="sxs-lookup"><span data-stu-id="0a983-113">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a983-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0a983-114">Return Value</span></span>  

 <span data-ttu-id="0a983-115">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="0a983-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a983-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a983-116">Remarks</span></span>  

 <span data-ttu-id="0a983-117">Необходимо указать только один из `filename` `pIStream` параметров или, но не оба.</span><span class="sxs-lookup"><span data-stu-id="0a983-117">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="0a983-118">Параметр `searchPath` не обязателен.</span><span class="sxs-lookup"><span data-stu-id="0a983-118">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a983-119">Требования</span><span class="sxs-lookup"><span data-stu-id="0a983-119">Requirements</span></span>  

 <span data-ttu-id="0a983-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0a983-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a983-121">См. также</span><span class="sxs-lookup"><span data-stu-id="0a983-121">See also</span></span>

- [<span data-ttu-id="0a983-122">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="0a983-122">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
