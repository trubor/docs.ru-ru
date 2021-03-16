---
title: Критическое изменение. Комплекты шифров TLS по умолчанию для .NET в Linux
description: Ознакомьтесь с критическим изменением в .NET 5, где .NET в Linux теперь учитывает конфигурацию OpenSSL для наборов шифров по умолчанию при выполнении шифрования TLS/SSL.
ms.date: 10/16/2020
ms.openlocfilehash: c28207aa5bf4324a7921deb006c57fbd5e1d6f5f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256820"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a>Комплекты шифров TLS по умолчанию для .NET в Linux

Теперь .NET для Linux учитывает конфигурацию OpenSSL для наборов шифров по умолчанию при выполнении шифрования TLS/SSL с помощью класса <xref:System.Net.Security.SslStream> или операций более высокого уровня, таких как HTTPS с помощью класса <xref:System.Net.Http.HttpClient>. Если комплекты шифров по умолчанию не настроены явно, .NET для Linux использует строго ограниченный список разрешенных комплектов шифров.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET не учитывается конфигурация системы для комплектов шифров по умолчанию. Список комплектов шифров по умолчанию для .NET в Linux является нестрогим.

Начиная с .NET 5 .NET для Linux учитывает конфигурацию OpenSSL для комплектов шифров по умолчанию, если она указана в файле *openssl.cnf*. Если комплекты шифров не настроены явно, единственными разрешенными комплектами шифров являются следующие:

- Комплекты шифров TLS 1.3
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

Поскольку это резервное значение по умолчанию не включает комплекты шифров, которые совместимы с TLS 1.0 или TLS 1.1, эти старые версии протоколов по умолчанию отключаются.

Если указано значение CipherSuitePolicy для SslStream для конкретного сеанса, по-прежнему будет заменяться содержимое файла конфигурации и (или) резервное значение по умолчанию .NET.

## <a name="reason-for-change"></a>Причина изменения

Пользователи, работающие с .NET для Linux, запрашивают изменение конфигурации по умолчанию для <xref:System.Net.Security.SslStream> на ту, которая обеспечивает высокую степень безопасности согласно результатам сторонних средств оценки.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Новые значения по умолчанию, скорее всего, будут работать при взаимодействии с современными клиентами или серверами. Если необходимо расширить список комплектов шифров по умолчанию для работы с устаревшими клиентами (или для взаимодействия с устаревшими серверами), укажите значение `CipherSuitePolicy` или измените файл конфигурации OpenSSL. Во многих дистрибутивах Linux файл конфигурации OpenSSL находится по пути */etc/ssl/openssl.cnf*.

В этом примере файл *openssl.cnf* определяет минимальный набор правил, эквивалентный заданной по умолчанию политике комплектов шифров для .NET 5 и более поздних версий для Linux. Вместо замены системного файла объедините эти понятия с файлом, который присутствует в вашей системе.

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

В дистрибутивах Red Hat Enterprise Linux, CentOS и Fedora в приложениях .NET по умолчанию используются комплекты шифров, разрешенные политиками шифрования на уровне системы. В этих дистрибутивах следует использовать конфигурацию политик шифрования вместо *openssl.cnf*.

## <a name="affected-apis"></a>Затронутые API

Невозможно обнаружить с помощью анализа API.

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
