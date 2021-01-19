---
title: Обзор пакета Azure SDK для .NET
description: Общие сведения о пакете Azure SDK для .NET и основные шаги по использованию этого пакета SDK в приложениях .NET
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b547e105b13d380ffae049ab55e76aa25abe8cc3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189204"
---
# <a name="azure-sdk-for-net-overview"></a><span data-ttu-id="2b7f3-103">Обзор пакета Azure SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="2b7f3-103">Azure SDK for .NET overview</span></span>

## <a name="what-is-the-azure-sdk-for-net"></a><span data-ttu-id="2b7f3-104">Что такое пакет Azure SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="2b7f3-104">What is the Azure SDK for .NET</span></span>

<span data-ttu-id="2b7f3-105">**Пакет Azure SDK для .NET** предназначен для упрощения использования служб Azure из приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-105">The **Azure SDK for .NET** is designed to make it easy to use Azure services from your .NET applications.</span></span>  <span data-ttu-id="2b7f3-106">Пакет Azure SDK для .NET предоставляет единообразный и привычный интерфейс для доступа к службам Azure при выполнении таких задач, как отправка и скачивание файлов из хранилища BLOB-объектов, получение секретов приложения из хранилища Azure Key Vault или обработка уведомлений из Центров событий Azure.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-106">Whether it is uploading and downloading files to Blob Storage, retrieving application secrets from Azure Key Vault, or processing notifications from Azure Event Hubs, the Azure SDK for .NET provides a consistent and familiar interface to access Azure services.</span></span>  

<span data-ttu-id="2b7f3-107">Пакет Azure SDK для .NET доступен в виде серии пакетов NuGet, которые можно использовать как в приложениях .NET Core (2.1 и более поздних версиях), так и в приложениях .NET Framework (4.6.1 и более поздних версиях).</span><span class="sxs-lookup"><span data-stu-id="2b7f3-107">The Azure SDK for .NET is available as series of NuGet packages that can be used in both .NET Core (2.1 and higher) and .NET Framework (4.6.1 and higher) applications.</span></span>

![Схема использования приложением .NET пакета Azure SDK для доступа к службам Azure](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a><span data-ttu-id="2b7f3-109">Использование пакета Azure SDK для .NET в приложениях</span><span class="sxs-lookup"><span data-stu-id="2b7f3-109">Use the Azure SDK for .NET in your applications</span></span>

<span data-ttu-id="2b7f3-110">Чтобы использовать пакет Azure SDK в приложении .NET, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-110">To use an Azure SDK package in one of your .NET applications, you want to follow these steps.</span></span>

1. <span data-ttu-id="2b7f3-111">**Найдите соответствующий пакет SDK.** Воспользуйтесь [списком пакетов](../packages.md), чтобы найти соответствующий пакет для службы Azure, с которой вы работаете.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-111">**Locate the appropriate SDK package -** Use the [package list](../packages.md) to find the appropriate package for the Azure service you are working with.</span></span>  <span data-ttu-id="2b7f3-112">Учтите, что у большинства служб есть клиентский пакет для работы со службой и пакет управления для создания экземпляров службы и управления ими.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-112">Be advised that most services have a client package for working with the service and a management package for creating and managing instances of the service.</span></span>  <span data-ttu-id="2b7f3-113">В большинстве случаев потребуется клиентский пакет.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-113">In most cases, you will want the client package.</span></span>  <span data-ttu-id="2b7f3-114">Установите этот пакет в приложении с помощью NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-114">Install this package in your application using NuGet.</span></span>

2. <span data-ttu-id="2b7f3-115">**Настройте проверку подлинности для приложения.** Для доступа к ресурсам Azure ваше приложение должно иметь соответствующие учетные данные и права доступа, назначенные в Azure.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-115">**Set up authentication for your application -** To access Azure resources, your application will need to have the appropriate credentials and access rights assigned in Azure.</span></span>  <span data-ttu-id="2b7f3-116">Сведения о настройке проверки подлинности см. в статье [Проверка подлинности приложений .NET в Azure](../authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2b7f3-116">Learn how to configure authentication in [Authenticating .NET applications to Azure](../authentication.md).</span></span>

3. <span data-ttu-id="2b7f3-117">**Напишите код в приложении с использованием пакета SDK.** При работе со службами Azure код сначала создает объект клиента для работы со службой, а затем вызывает методы этого клиентского объекта для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-117">**Write code using the SDK in your application -** When working with Azure services, your code will first create a client object to work with the service and then call methods on that client object to interact with the service.</span></span>  <span data-ttu-id="2b7f3-118">Предоставляются как синхронные, так и асинхронные методы.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-118">Both synchronous and asynchronous methods are provided.</span></span>  <span data-ttu-id="2b7f3-119">Примеры использования каждого отдельного пакета SDK приведены в документации по Azure.</span><span class="sxs-lookup"><span data-stu-id="2b7f3-119">Examples of using each individual SDK package are provided throughout the Azure documentation.</span></span>

4. <span data-ttu-id="2b7f3-120">**Настройте ведение журнала для пакета SDK (необязательно).** Если необходимо диагностировать проблемы взаимодействия приложения и Azure, можно [включить ведение журнала в пакете Azure SDK для .NET](../logging.md).</span><span class="sxs-lookup"><span data-stu-id="2b7f3-120">**Configure logging for the SDK (optional) -** If you need to diagnose issues between your application and Azure, you can [enable logging in the Azure SDK for .NET](../logging.md).</span></span>
