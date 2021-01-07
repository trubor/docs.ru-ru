---
title: Шифрование и безопасность сети — gRPC для разработчиков WCF
description: Некоторые замечания по сетевой безопасности и шифрованию в gRPC
ms.date: 01/06/2021
ms.openlocfilehash: cf4d30ff862e64aadfeacf45ed3768fc14737800
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970145"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="ad97d-103">Шифрование и безопасность сети</span><span class="sxs-lookup"><span data-stu-id="ad97d-103">Encryption and network security</span></span>

<span data-ttu-id="ad97d-104">Модель сетевой безопасности для Windows Communication Foundation (WCF) является обширной и сложной.</span><span class="sxs-lookup"><span data-stu-id="ad97d-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="ad97d-105">Она включает безопасность на уровне транспорта с помощью HTTPS или TLS-over-TCP и безопасность на уровне сообщений, используя спецификацию WS-Security для шифрования отдельных сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad97d-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="ad97d-106">gRPC оставляет защищенную сеть основным протоколом HTTP/2, который можно защитить с помощью TLS-сертификатов.</span><span class="sxs-lookup"><span data-stu-id="ad97d-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="ad97d-107">Веб-браузеры настаивает на использовании соединений TLS для HTTP/2, но большинство программных клиентов, включая. NET `HttpClient` может использовать HTTP/2 через незашифрованные соединения.</span><span class="sxs-lookup"><span data-stu-id="ad97d-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span>

<span data-ttu-id="ad97d-108">Для общедоступных API следует всегда использовать TLS-подключения и предоставлять действительные сертификаты для служб из соответствующего центра SSL.</span><span class="sxs-lookup"><span data-stu-id="ad97d-108">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="ad97d-109">[Летсенкрипт](https://letsencrypt.org) предоставляет бесплатные, АВТОМАТИЗИРОВАНные SSL-сертификаты и большинство современных инфраструктур размещения поддерживает стандарт летсенкрипт с общими подключаемыми модулями или расширениями.</span><span class="sxs-lookup"><span data-stu-id="ad97d-109">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="ad97d-110">Для внутренних служб в корпоративной сети по-прежнему следует использовать TLS для защиты сетевого трафика от gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="ad97d-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="ad97d-111">Если необходимо использовать явный протокол TLS между службами, работающими в Kubernetes, рассмотрите возможность использования центра сертификации в кластере и контроллера диспетчера сертификатов, например [CERT-Manager](https://docs.cert-manager.io/en/latest/).</span><span class="sxs-lookup"><span data-stu-id="ad97d-111">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="ad97d-112">Затем можно автоматически назначать сертификаты службам во время развертывания.</span><span class="sxs-lookup"><span data-stu-id="ad97d-112">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ad97d-113">[Назад](channel-credentials.md)
>[Вперед](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="ad97d-113">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
