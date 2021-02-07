---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: GetDebugInfo'
title: Метод ISymUnmanagedWriter::GetDebugInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: 2255cc90c0bfcd36dacdf81703af67d3f47739db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762322"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="8267a-103">Метод ISymUnmanagedWriter::GetDebugInfo</span><span class="sxs-lookup"><span data-stu-id="8267a-103">ISymUnmanagedWriter::GetDebugInfo Method</span></span>

<span data-ttu-id="8267a-104">Возвращает сведения, необходимые компилятору для записи записи каталога отладки в заголовке переносимого исполняемого файла (PE).</span><span class="sxs-lookup"><span data-stu-id="8267a-104">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="8267a-105">Средство записи символов заполняет все поля, за исключением `TimeDateStamp` и `PointerToRawData` .</span><span class="sxs-lookup"><span data-stu-id="8267a-105">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="8267a-106">(Компилятор отвечает за установку этих двух полей соответствующим образом.)</span><span class="sxs-lookup"><span data-stu-id="8267a-106">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="8267a-107">Компилятор должен вызывать этот метод, выдавать большой двоичный объект данных в PE-файл, устанавливать `PointerToRawData` поле в IMAGE_DEBUG_DIRECTORY, чтобы указывать на выпущенные данные, и записывать IMAGE_DEBUG_DIRECTORY в PE-файл.</span><span class="sxs-lookup"><span data-stu-id="8267a-107">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="8267a-108">Компилятор также должен задать `TimeDateStamp` для поля значение, равное значению `TimeDateStamp` создаваемого PE.</span><span class="sxs-lookup"><span data-stu-id="8267a-108">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8267a-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8267a-109">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8267a-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="8267a-110">Parameters</span></span>  

 `pIDD`  
 <span data-ttu-id="8267a-111">[вход, выход] Указатель на IMAGE_DEBUG_DIRECTORY, который средство записи символов будет заполнять.</span><span class="sxs-lookup"><span data-stu-id="8267a-111">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="8267a-112">окне Значение типа `DWORD` , содержащее размер данных отладки.</span><span class="sxs-lookup"><span data-stu-id="8267a-112">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="8267a-113">заполняет Указатель на объект `DWORD` , который получает размер буфера, необходимого для хранения данных отладки.</span><span class="sxs-lookup"><span data-stu-id="8267a-113">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="8267a-114">заполняет Указатель на буфер, достаточно большой для хранения отладочных данных для хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="8267a-114">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8267a-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8267a-115">Return Value</span></span>  

 <span data-ttu-id="8267a-116">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8267a-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8267a-117">Требования</span><span class="sxs-lookup"><span data-stu-id="8267a-117">Requirements</span></span>  

 <span data-ttu-id="8267a-118">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8267a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8267a-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8267a-119">See also</span></span>

- [<span data-ttu-id="8267a-120">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="8267a-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
