---
description: 'Дополнительные сведения о методе ICorDebugType:: GetStaticFieldValue'
title: Метод ICorDebugType::GetStaticFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 378c72f24fedd76f40704ff684781bed124055bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658234"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="8b62a-103">Метод ICorDebugType::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="8b62a-103">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="8b62a-104">Возвращает указатель интерфейса на объект ICorDebugValue, содержащий значение статического поля, на которое ссылается заданный токен поля в указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="8b62a-104">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b62a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8b62a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b62a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8b62a-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="8b62a-107">окне `mdFieldDef` Токен, указывающий статическое поле.</span><span class="sxs-lookup"><span data-stu-id="8b62a-107">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="8b62a-108">окне Указатель на объект ICorDebugFrame, представляющий кадр стека.</span><span class="sxs-lookup"><span data-stu-id="8b62a-108">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8b62a-109">заполняет Указатель на адрес объекта `ICorDebugValue` , который содержит значение статического поля.</span><span class="sxs-lookup"><span data-stu-id="8b62a-109">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b62a-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="8b62a-110">Remarks</span></span>  

 <span data-ttu-id="8b62a-111">`GetStaticFieldValue`Метод может использоваться только в том случае, если тип имеет значение ELEMENT_TYPE_CLASS или ELEMENT_TYPE_VALUETYPE, как указано в методе [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8b62a-111">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="8b62a-112">Для неуниверсальных типов операция, выполняемая, `GetStaticFieldValue` идентична вызову [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) для объекта ICorDebugClass, возвращаемого командлетом [ICorDebugType::](icordebugtype-getclass-method.md)GetObject.</span><span class="sxs-lookup"><span data-stu-id="8b62a-112">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="8b62a-113">Для универсальных типов значение статического поля будет относиться к определенному экземпляру.</span><span class="sxs-lookup"><span data-stu-id="8b62a-113">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="8b62a-114">Кроме того, если статическое поле может быть связано с потоком, контекстом или доменом приложения, то кадр стека поможет отладчику определить правильное значение.</span><span class="sxs-lookup"><span data-stu-id="8b62a-114">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b62a-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="8b62a-115">Remarks</span></span>  

 <span data-ttu-id="8b62a-116">`GetStaticFieldValue` может использоваться, только если вызов `ICorDebugType::GetType` возвращает значение ELEMENT_TYPE_CLASS или ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="8b62a-116">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b62a-117">Требования</span><span class="sxs-lookup"><span data-stu-id="8b62a-117">Requirements</span></span>  

 <span data-ttu-id="8b62a-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b62a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b62a-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b62a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b62a-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b62a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b62a-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b62a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
