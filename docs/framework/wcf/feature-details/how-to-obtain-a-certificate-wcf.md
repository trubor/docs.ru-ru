---
description: Дополнительные сведения о том, как получить сертификат (WCF).
title: Практическое руководство. Получение сертификата (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: dad44776819f9d026445689e072e4aa5059d54fb
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494809"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Практическое руководство. Получение сертификата (WCF)

Чтобы использовать любую из функций Windows Communication Foundation (WCF), использующих сертификаты X. 509, сначала нужно получить сертификаты.  
  
## <a name="obtain-an-x509-certificate"></a>Получение сертификата X. 509  
  
Выберите один из следующих вариантов.  
  
- Приобретите сертификат в центре сертификации, например VeriSign, Inc.  
  
- Создайте собственную службу сертификатов и настройте ее так, чтобы центр сертификации подписывал сертификаты. Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter и Windows 2000 Datacenter Server включают службы сертификации, поддерживающие инфраструктуру открытых ключей (PKI). В Windows Server 2008 для управления центром сертификации используется [Active Directory роль служб сертификации](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) .  
  
- Создайте собственную службу сертификатов и не настраивайте подпись сертификатов.  
  
> [!NOTE]
> Независимо от того, какой способ выбран, получатель запроса SOAP, который содержит сертификат X.509, должен доверять сертификату X.509. Это означает, что сертификат X.509 или издатель в цепи сертификатов находится в хранилище сертификатов "Доверенные лица" и сертификат X.509 не помещен в хранилище ненадежных сертификатов.  
  
## <a name="see-also"></a>См. также раздел

- [Работа с сертификатами](working-with-certificates.md)
- [Практическое руководство. Создание временных сертификатов для использования во время разработки](how-to-create-temporary-certificates-for-use-during-development.md)
