---
description: 'Узнайте подробнее о: Authenticode (справочник по неуправляемым интерфейсам API)'
title: Authenticode (справочник по неуправляемым интерфейсам API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 0a4a9b4ba3cc9a5818896508c80bc31073f514e7
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027848"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (справочник по неуправляемым интерфейсам API)

Поддерживает модуль создания и проверки лицензий Authenticode XrML.  
  
## <a name="in-this-section"></a>в этом разделе  

 [Функция _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Получает хэш SHA-1 открытого ключа, связанного с закрытым ключом, который используется для подписания указанного сертификата.  
  
 [Функция _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Вычисляет токен открытого ключа строгого имени из формата CSP PUBLICKEYBLOB.  
  
 [Функция _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Преобразует модули и экспоненту в строгое имя маркера открытого ключа.  
  
 [Функция CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Функция CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Освобождает ресурсы, выделенные для структуры AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Функция CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Присваивает метки времени лицензии Authenticode XrML, созданной функцией CertCreateAuthenticodeLicense.  
  
 [Функция CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Проверяет правильность лицензии Authenticode XrML.  
  
 [Структура AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Определяет информацию о подписавшем Authenticode.  
  
 [Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Определяет информацию об отметке времени Authenticode.  

## <a name="requirements"></a>Требования

**Библиотека**: clr.dll
  
## <a name="see-also"></a>См. также раздел

- [Справочник по неуправляемым API](../index.md)
