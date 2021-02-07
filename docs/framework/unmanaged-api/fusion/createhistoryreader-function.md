---
description: Дополнительные сведения о функции Креатехисториреадер
title: Функция CreateHistoryReader
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 0943f3d0f3322d34ed92c0a96b909e4d63ec5e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761126"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="d8556-103">Функция CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="d8556-103">CreateHistoryReader Function</span></span>

<span data-ttu-id="d8556-104">Создает средство чтения журнала для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="d8556-104">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8556-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8556-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8556-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8556-106">Parameters</span></span>  

 `wzFilePath`  
 <span data-ttu-id="d8556-107">окне Путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="d8556-107">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="d8556-108">заполняет При успешном завершении содержит указатель на средство чтения журнала.</span><span class="sxs-lookup"><span data-stu-id="d8556-108">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8556-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d8556-109">Return Value</span></span>  

 <span data-ttu-id="d8556-110">Этот метод возвращает стандартные коды ошибок COM, определенные в файле WinError. h, а также значения, описанные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="d8556-110">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="d8556-111">Код возврата</span><span class="sxs-lookup"><span data-stu-id="d8556-111">Return code</span></span>|<span data-ttu-id="d8556-112">Описание</span><span class="sxs-lookup"><span data-stu-id="d8556-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d8556-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8556-113">S_OK</span></span>|<span data-ttu-id="d8556-114">Указывает, что метод успешно завершен.</span><span class="sxs-lookup"><span data-stu-id="d8556-114">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="d8556-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d8556-115">E_INVALIDARG</span></span>|<span data-ttu-id="d8556-116">Указывает, что `wzFilePath` или `ppHistoryReader` задана пустая ссылка.</span><span class="sxs-lookup"><span data-stu-id="d8556-116">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8556-117">Требования</span><span class="sxs-lookup"><span data-stu-id="d8556-117">Requirements</span></span>  

 <span data-ttu-id="d8556-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8556-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8556-119">**Библиотека:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="d8556-119">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="d8556-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8556-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8556-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d8556-121">See also</span></span>

- [<span data-ttu-id="d8556-122">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="d8556-122">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
