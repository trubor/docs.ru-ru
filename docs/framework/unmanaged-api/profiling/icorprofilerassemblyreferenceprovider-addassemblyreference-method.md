---
description: 'Дополнительные сведения о методе: ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference'
title: Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: e73a6d59b76744dcf9f4991be2589220669e154d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760748"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference

[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]  
  
 Информирует среду CLR о ссылке сборки, которую профилировщик планирует добавить в обратный вызов [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Параметры

`pAssemblyRefInfo` Указатель на структуру [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) , которая предоставляет среде CLR сведения о ссылке на сборку, которую следует учитывать при выполнении анализа закрытия ссылок на сборки.
  
## <a name="remarks"></a>Remarks  

 Профилировщик вызывает этот метод для каждой целевой сборки, на которую планируется ссылаться из сборки, указанной в `wszAssemblyPath` аргументе обратного вызова [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) . Объект интерфейса [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) передается обратному вызову [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) профилировщика вместе с путем к сборке и именем в `wszAssemblyPath` аргументе.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)
- [Метод GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)
- [Метод ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)
