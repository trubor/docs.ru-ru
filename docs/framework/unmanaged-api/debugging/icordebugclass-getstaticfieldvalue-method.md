---
description: 'Дополнительные сведения о методе: ICorDebugClass:: GetStaticFieldValue'
title: Метод ICorDebugClass::GetStaticFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: a5406e44491ce89030731c35752066e4943cebfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711527"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="381d3-103">Метод ICorDebugClass::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="381d3-103">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="381d3-104">Возвращает значение указанного статического поля.</span><span class="sxs-lookup"><span data-stu-id="381d3-104">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="381d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381d3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="381d3-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="381d3-107">окне Токен поля `Def` , ссылающийся на извлекаемое поле.</span><span class="sxs-lookup"><span data-stu-id="381d3-107">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="381d3-108">окне Указатель на объект ICorDebugFrame, представляющий кадр, который будет использоваться для однозначного определения статических элементов потока, контекста или домена приложения.</span><span class="sxs-lookup"><span data-stu-id="381d3-108">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="381d3-109">Если статическое поле задается относительно потока, контекста или домена приложения, кадр определит правильное значение.</span><span class="sxs-lookup"><span data-stu-id="381d3-109">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="381d3-110">заполняет Указатель на адрес объекта ICorDebugValue, который представляет значение статического поля.</span><span class="sxs-lookup"><span data-stu-id="381d3-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381d3-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="381d3-111">Remarks</span></span>  

 <span data-ttu-id="381d3-112">Для параметризованных типов значение статического поля задается относительно конкретного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="381d3-112">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="381d3-113">Поэтому, если конструктор класса принимает параметры типа <xref:System.Type> , вызовите метод [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) вместо `ICorDebugClass::GetStaticFieldValue` .</span><span class="sxs-lookup"><span data-stu-id="381d3-113">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381d3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="381d3-114">Requirements</span></span>  

 <span data-ttu-id="381d3-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381d3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381d3-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="381d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="381d3-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="381d3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="381d3-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
