---
title: Стандартный блок секретов ДАПР
description: Описание стандартного блока секретов, его функций, преимуществ и способов применения
author: edwinvw
ms.date: 02/17/2021
ms.openlocfilehash: 52b899b4d496aab6762f69bbee99faecfcd23d59
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623750"
---
# <a name="the-dapr-secrets-building-block"></a>Стандартный блок секретов ДАПР

Для корпоративных приложений требуются секреты. Ниже приведены распространенные примеры.

- Строка подключения к базе данных, которая содержит имя пользователя и пароль.
- Ключ API для вызова внешнего веб-API.
- Сертификат клиента для проверки подлинности во внешней системе.

Секреты должны тщательно управляться, чтобы они никогда не раскрываются вне приложения.

Не давно, мы популярны хранить секреты приложений в файле конфигурации внутри базы кода приложения. Разработчики .NET будут любовью файл *web.config* . В то время как простота реализации, интеграция секретов в вместе с кодом была далеко из безопасности. Распространенным вамом был включение файла при отправке в общедоступный репозиторий GIT с предоставлением секретов в мире.

Широко принятой методологией для создания современных распределенных приложений является [Twelve-Factorное приложение](https://12factor.net/). Он описывает набор принципов и рекомендации. Третий фактор предписывает, что *Конфигурация и секреты должны быть внешними вне базы кода.*

Чтобы решить эту проблему, платформа .NET Core включает функцию [диспетчера секретов](/aspnet/core/security/app-secrets#secret-manager) , которая хранит конфиденциальные данные в физической папке за пределами дерева проекта. Хотя секреты находятся за пределами системы управления версиями, эта функция не шифрует данные. Он предназначен только для **целей разработки** .

Более современная и безопасной практикой является изоляция секретов в средстве управления секретами, например **Hashicorp Vault** или **Azure Key Vault**.  Эти средства позволяют хранить секреты извне, изменять учетные данные в разных средах и ссылаться на них из кода приложения. Однако каждый инструмент имеет свои сложности и обученную кривую.

ДАПР предлагает стандартный блок, упрощающий управление секретами.

## <a name="what-it-solves"></a>Решение

[Стандартный блок ДАПР секреты](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) абстрагирует сложность работы с секретными и секретными средствами управления.

- Он скрывает базовые коммуникации через единый интерфейс.
- Он поддерживает различные *подключаемые* компоненты хранилища секретов, которые могут различаться в зависимости от разработки и рабочей среды.
- Приложениям не требуются прямые зависимости от библиотек хранилища секретов.
- Разработчикам не требуются подробные сведения о каждом хранилище секретов.

ДАПР обрабатывает все перечисленные выше проблемы.

Доступ к секретам обеспечивается с помощью проверки подлинности и авторизации. Доступ к секретам может получить только приложение с достаточными правами. Приложения, работающие в Kubernetes, могут также использовать встроенный механизм управления секретами.

## <a name="how-it-works"></a>Принцип работы

Приложения используют стандартный блок секреты двумя способами:

- Получение секрета непосредственно из блока приложения.
- Косвенная ссылка на секрет из конфигурации компонента ДАПР.

Извлечение секретов напрямую рассматривается в первую очередь. Ссылка на секрет из файла конфигурации компонента ДАПР описана в следующем разделе.

Приложение взаимодействует с ДАПР расширения при использовании стандартного блока секретов. Расширения предоставляет API секретов. API можно вызывать с помощью HTTP или gRPC. Используйте следующий URL-адрес для вызова API HTTP:

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

URL-адрес содержит следующие сегменты:

- `<dapr-port>` Указывает номер порта, на котором прослушивается расширения ДАПР.
- `<store-name>` Указывает имя хранилища секретов ДАПР.
- `<name>` Указывает имя секрета для извлечения.
- `<metadata>` предоставляет дополнительные сведения о секрете. Этот сегмент является необязательным, и свойства метаданных различаются для хранилища секретов. Дополнительные сведения о свойствах метаданных см. в [справочнике по API секретов]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).

 > [!NOTE]
 > Приведенный выше URL-адрес представляет собственный вызов API ДАПР, доступный для любой платформы разработки, поддерживающей HTTP или gRPC. Популярные платформы, такие как .NET, Java и Go, имеют собственные пользовательские API.

Ответ JSON содержит ключ и значение секрета.

На рис. 10-1 показано, как ДАПР обрабатывает запрос для API секретов:

![Схема получения секрета с помощью API секретов ДАПР.](media/secrets/secrets-flow.png)

**Рис. 10-1**. Получение секрета с помощью API секретов ДАПР.

1. Служба вызывает ДАПР секреты API, а также имя хранилища секретов и секрет для получения.
1. ДАПР расширения извлекает указанный секрет из хранилища секретов.
1. ДАПР расширения возвращает секретную информацию обратно в службу.

В некоторых хранилищах секретов поддерживается хранение нескольких пар "ключ-значение" в одном секрете. В этих сценариях ответ будет содержать несколько пар "ключ-значение" в одном ответе JSON, как показано в следующем примере:

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

API ДАПР Secrets также предоставляет операцию для получения всех секретов, к которым приложение имеет доступ.

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a>Использование пакета SDK для ДАПР .NET

Для разработчиков .NET пакет SDK для ДАПР .NET упрощает управление секретами ДАПР. Рассмотрим `DaprClient.GetSecretAsync` метод. Он позволяет получить секрет непосредственно из любого хранилища секретов ДАПР с минимальными усилиями. Ниже приведен пример выборки секрета строки подключения для базы данных SQL Server:

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

`GetSecretAsync`Ниже приведены аргументы для метода.

- Имя компонента хранилища секретов ДАПР ("Secret-Store")
- Секрет для извлечения ("ешопсекретс")
- Необязательные пары "ключ-значение" метаданных ("version_id = 3")

Метод реагирует на объект Dictionary в качестве секрета, который может содержать несколько пар "ключ-значение". В приведенном выше примере `customerdb` для возвращения строки подключения в коллекции упоминается секрет с именем.

В пакете SDK для ДАПР .NET также реализован поставщик конфигурации .NET. Загружает указанные секреты в базовый [API конфигурации .NET Core](../../core/extensions/configuration.md). Затем работающее приложение может ссылаться на секреты из `IConfiguration` словаря, зарегистрированного в ASP.NET Core внедрения зависимостей.

Поставщик конфигурации секретов доступен из пакета NuGet [Dapr.Extensions.Configфигурации](https://www.nuget.org/packages/Dapr.Extensions.Configuration) . Поставщик можно зарегистрировать в `Program.cs` веб-API ASP.NET приложении:  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

Приведенный выше пример загружает `eshopsecrets` коллекцию секретов в систему конфигурации .NET при запуске. Для регистрации поставщика требуется экземпляр `DaprClient` для вызова API секретов на ДАПР расширения. Другие аргументы включают имя хранилища секретов и `DaprSecretDescriptor` объект с именем секрета.

После загрузки вы можете получить секреты непосредственно из кода приложения:

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a>Компоненты хранилища секретов

Стандартный блок секреты поддерживает несколько компонентов хранилища секретов. На момент написания статьи доступны следующие хранилища секретов:

- Переменные среды
- Локальный файл
- Секреты Kubernetes
- Диспетчер секретов AWS
- Хранилище ключей Azure;
- Диспетчер секретов обеспечить
- Хранилище HashiCorp

> [!IMPORTANT]
> Переменные среды и компоненты локальных файлов предназначены только для рабочих нагрузок разработки.

В следующих разделах показано, как настроить хранилище секретов.

### <a name="configuration"></a>Параметр Configuration

Вы настраиваете хранилище секретов с помощью файла конфигурации компонента ДАПР. Ниже показана типичная структура файла.

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

Для всех файлов конфигурации компонентов ДАПР требуется указать `name` вместе с необязательным `namespace` значением. Кроме того, `type` поле в `spec` разделе указывает тип компонента хранилища секретов. Свойства в `metadata` разделе различаются для каждого хранилища секретов.

### <a name="indirectly-consume-dapr-secrets"></a>Косвенно использовать секреты ДАПР

Как упоминалось ранее в этой главе, приложения могут также использовать секреты, ссылаясь на них в файлах конфигурации компонентов. Рассмотрим [компонент управления состоянием](state-management.md) , который использует кэш Redis для хранения состояния:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

Приведенный выше файл конфигурации содержит пароль в формате **открытого текста** для подключения к серверу Redis. **Жестко** зафиксированные пароли всегда являются неправильными идеями. При принудительной отправке этого файла конфигурации в общедоступный репозиторий будет предоставляться пароль. Сохранение пароля в секретном хранилище значительно улучшит этот сценарий.

В следующих примерах это демонстрируется с помощью нескольких разных хранилищ секретов.

### <a name="local-file"></a>Локальный файл

Компонент локального файла предназначен для сценариев разработки. Он сохраняет секреты в локальной файловой системе внутри JSON-файла. Ниже приведен пример с именем `eshop-secrets.json` . Он содержит один секретный пароль для Redis:

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

Этот файл помещается в `components` папку, указанную при запуске приложения ДАПР.

Следующий файл конфигурации хранилища секретов использует JSON-файл в качестве хранилища секретов. Он также помещается в `components` папку:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

Тип компонента — `secretstore.local.file` . `secretsFile`Элемент Metadata указывает путь к секретному файлу.

> [!IMPORTANT]
> Путь к секретному файлу может быть абсолютным или относительным. Относительный путь основан на папке, в которой запускается приложение. В этом примере `components` Папка является вложенной папкой каталога, содержащего приложение .NET.

В папке приложения запустите приложение ДАПР, указав `components` путь в качестве аргумента командной строки:

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> Приведенный выше пример применяется к запуску ДАПР в собственном режиме. Для размещения Kubernetes рекомендуется использовать подключения томов.

`nestedSeparator`В файле конфигурации ДАПР указывает символ для *СПРЯМЛЕНИЯ* иерархии JSON. Рассмотрим следующий фрагмент кода:

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

Используя двоеточие в качестве разделителя, можно получить `customerdb` строку соединения с помощью ключа `connectionStrings:customerdb` .

> [!NOTE]
> Двоеточие `:` является значением разделителя по умолчанию.

В следующем примере файл конфигурации управления состоянием ссылается на локальный компонент хранилища секретов, чтобы получить пароль для подключения к серверу Redis:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

`secretKeyRef`Элемент ссылается на секрет, содержащий пароль. Он заменяет более раннее значение *clear-Text* . Имя секрета и имя ключа, которые `eShopRedisPassword` ссылаются на секрет. Имя компонента управления секретами `eshop-local-secret-store` находится в `auth` элементе Metadata.

Может возникнуть вопрос, почему `eShopRedisPassword` он идентичен как для имени, так и для ключа в ссылке на секрет. В хранилище секретов локального файла секреты не идентифицируются с отдельным именем. Сценарий будет отличаться в следующем примере с использованием секретов Kubernetes.

### <a name="kubernetes-secret"></a>Секрет Kubernetes

Во втором примере основное внимание уделяется ДАПР приложению, работающему в Kubernetes. Он использует стандартный механизм секреты, Kubernetes предложения. Используйте интерфейс командной строки Kubernetes ( `kubectl` ), чтобы создать секрет с именем `eshop-redis-secret` , который содержит пароль:

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

После создания можно сослаться на секрет в файле конфигурации компонента для управления состоянием:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

`secretKeyRef`Элемент указывает имя секрета Kubernetes и ключ секрета, `eshopsecrets` и `redisPassword` соответственно. `auth`Раздел Metadata указывает ДАПР использовать компонент управления секретами Kubernetes.

> [!NOTE]
> Проверка подлинности является значением по умолчанию при использовании секретов Kubernetes и может быть опущено.

В рабочем параметре секреты обычно создаются как часть автоматизированного конвейера CI/CD. Это гарантирует, что только пользователи с достаточными разрешениями смогут получить доступ к секретам и изменить их. Разработчики создают файлы конфигурации, не зная фактического значения секретов.

### <a name="azure-key-vault"></a>Хранилище ключей Azure;

Следующий пример предназначен для работы в реальном рабочем сценарии. В нем используется **Azure Key Vault** в качестве хранилища секретов. Azure Key Vault — это управляемая служба Azure, которая позволяет безопасно хранить секреты в облаке.

Для работы этого примера необходимо выполнить следующие условия.

- Вы защитили административный доступ к подписке Azure.
- Вы подготовили Azure Key Vault с именем `eshopkv` , содержащее секрет с именем `redisPassword` , который содержит пароль для подключения к серверу Redis.
- Вы создали [субъект-службу](/azure/active-directory/develop/howto-create-service-principal-portal) в Azure Active Directory.
- Вы установили сертификат X509 для этого субъекта-службы (содержащий открытый и закрытый ключи) в локальной файловой системе.

> [!NOTE]
> Субъект-служба — это удостоверение, которое может использоваться приложением для проверки подлинности службы Azure. Субъект-служба использует сертификат X509. Приложение использует этот сертификат в качестве учетных данных для проверки подлинности.

В [документации по хранилищу секретов дапр Azure Key Vault](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) содержатся пошаговые инструкции по созданию и настройке среды Key Vault.

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a>Использование Key Vault при работе в автономном режиме

Для использования Azure Key Vault в режиме автономного размещения ДАПР требуется следующий файл конфигурации:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

Тип хранилища секретов — `secretstores.azure.keyvault` . `metadata`Элемент, для которого необходимо настроить доступ к Key Vault, требует следующих свойств:

- `vaultName`Содержит имя Azure Key Vault.
- `spnTenantId`Содержит *идентификатор клиента* субъекта-службы, используемого для проверки подлинности в Key Vault.
- `spnClientId`Содержит *идентификатор приложения* субъекта-службы, используемого для проверки подлинности в Key Vault.
- `spnCertificateFile`Содержит путь к файлу сертификата субъекта-службы для проверки подлинности в Key Vault.

> [!TIP]
> Сведения о субъекте-службе можно скопировать из портал Azure или Azure CLI.

Теперь приложение может получить пароль Redis из Azure Key Vault.

#### <a name="use-key-vault-when-running-on-kubernetes"></a>Использование Key Vault при выполнении в Kubernetes

Для использования Azure Key Vault с ДАПР и Kubernetes также требуется субъект-служба для проверки подлинности Azure Key Vault.

Сначала создайте *секрет Kubernetes* , который содержит файл сертификата, с помощью средства CLI kubectl:

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

Команда требует два аргумента командной строки:

- `[k8s_spn_secret_name]` — Это имя секрета в хранилище секретов Kubernetes.
- `[pfx_certificate_file_local_path]` путь к файлу сертификата X509.

После создания можно сослаться на секрет Kubernetes в файле конфигурации компонента хранилища секретов:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

На этом этапе приложение, работающее в Kubernetes, может получить пароль Redis из Azure Key Vault.

> [!IMPORTANT]
> Очень важно, чтобы файл сертификата X509 для субъекта-службы оставался в надежном месте. Его лучше разместить в хорошо известной папке за пределами репозитория исходного кода. Затем файл конфигурации может ссылаться на файл сертификата из этой хорошо известной папки. На локальном компьютере разработки вы несете ответственность за копирование сертификата в папку. Для автоматизированных развертываний конвейер скопирует сертификат на компьютер, на котором развернуто приложение. Рекомендуется использовать другой субъект-службу для каждой среды. Таким образом, субъект-служба из среды разработки не сможет получить доступ к секретам в рабочей среде.

При работе в службе Azure Kubernetes Service (AKS) предпочтительнее использовать [управляемое удостоверение Azure](/azure/active-directory/managed-identities-azure-resources/overview) для проверки подлинности в Azure Key Vault. Управляемые удостоверения выходят за рамки этой книги, но описаны в документации [Azure Key Vault с управляемыми удостоверениями](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) .

### <a name="scope-secrets"></a>Секреты области

Области секрета позволяют контролировать, к каким секретам имеет доступ приложение. Вы настраиваете области в файле конфигурации ДАПР расширения. В [документации по конфигурации ДАПР](https://docs.dapr.io/operations/configuration/configuration-overview/) содержатся инструкции по области секретов.

Ниже приведен пример файла конфигурации ДАПР расширения, который содержит области секрета:

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

Вы указываете области для каждого хранилища секретов. В приведенном выше примере хранилище секретов имеет имя `eshop-azurekv-secret-store` . Вы настраиваете доступ к секретам, используя следующие свойства:

| Свойство         | Значение               | Описание                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | `allow` или `deny`   | Разрешает или запрещает доступ ко *всем* секретам в указанном хранилище секретов. Это свойство является необязательным и имеет значение по умолчанию `allow` . |
| `allowedSecrets` | Список секретных ключей | Секреты, указанные в массиве, будут доступны. Это необязательное свойство.                                                     |
| `deniedSecrets`  | Список секретных ключей | Секретные данные, указанные в массиве, будут недоступны. Это необязательное свойство.                                                 |

`allowedSecrets`Свойства и `deniedSecrets` имеют приоритет над `defaultAccess` свойством. Представьте `defaultAccess: allowed` , как указать и `allowedSecrets` список. В этом случае приложение будет доступно только для секретов в `allowedSecrets` списке.

## <a name="reference-application-eshopondapr"></a>Эталонное приложение: Ешопондапр

В эталонном приложении Ешопондапр используется стандартный блок секреты для двух секретов:

- Пароль для подключения к кэшу Redis.
- Ключ API для использования API Twilio Sendgrid. Приложение использует Твиллио для отправки сообщений электронной почты с помощью выходной привязки ДАПР (как описано в [главе стандартные блоки привязки](bindings.md)).

При запуске приложения с помощью Docker Compose используется хранилище секретов **локального файла** . Файл конфигурации компонента находится `eshop-secretstore.yaml` в `dapr/components` папке репозитория ешопондапр:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

Файл конфигурации ссылается на локальный файл хранилища `eshop-secretstore.json` , расположенный в той же папке:

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

`components`Папка указывается в командной строке и монтируется в качестве локальной папки в контейнере ДАПР расширения. Ниже приведен фрагмент `docker-compose.override.yml` файла в корне репозитория, указывающий подключение тома.

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> Файл переопределения Docker Compose содержит значения конфигурации, зависящие от среды.

Параметр `/components` подключения тома и `--components-path` командной строки передается в `daprd` команду Startup.

После настройки другие файлы конфигурации компонентов также могут ссылаться на секреты. Ниже приведен пример конфигурации компонента публикации или подписки, которая использует секреты:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

В предыдущем примере для ссылки на секреты используется локальное хранилище Redis.

## <a name="summary"></a>Итоги

Стандартный блок ДАПР Secrets предоставляет возможности хранения и извлечения конфиденциальных параметров конфигурации, таких как пароли и строки подключения. Он сохраняет секретные данные в частном порядке и предотвращает их случайное раскрываемое.

Стандартный блок поддерживает несколько разных хранилищ секретов и скрывает их сложность с помощью API секретов ДАПР.

Пакет SDK для ДАПР .NET предоставляет `DaprClient` объект для получения секретов. Он также включает поставщик конфигурации .NET, который добавляет секреты в систему конфигурации .NET Core. После загрузки вы можете использовать эти секреты в коде .NET.

Вы можете использовать области секрета для управления доступом к конкретным секретам.

## <a name="references"></a>Ссылки

- [За пределами приложения Twelve-Factor](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
>[Назад](observability.md)
>[Вперед](summary.md)
