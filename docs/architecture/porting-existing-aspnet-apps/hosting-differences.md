---
title: Различия в размещении между ASP.NET MVC и ASP.NET Core
description: Обзор различий между размещением приложений ASP.NET MVC и ASP.NET Core приложениями.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9881a40403f8109fa63e25167b753ed4ce8ade17
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122902"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a>Различия в размещении между ASP.NET MVC и ASP.NET Core

Приложения ASP.NET MVC размещаются в IIS и могут полагаться на конфигурацию IIS для их поведения. Это часто включает [модули IIS](/iis/get-started/introduction-to-iis/iis-modules-overview). В рамках проверки приложения, чтобы подготовиться к его переносу из ASP.NET MVC в ASP.NET Core, команды должны выбрать, какие модули, если они используются, из списка модулей IIS, установленных на сервере.

[ASP.NET Core приложения могут выполняться на нескольких разных серверах](/aspnet/core/fundamentals/servers/). По умолчанию для кросс-платформенного сервера Kestrel является хорошим выбором. Приложения, работающие в Kestrel, могут размещаться в службах IIS, выполняющихся в отдельном процессе. В Windows приложения также могут выполняться в процессе в службах IIS или с помощью HTTP.sys. Как правило, для оптимальной производительности рекомендуется Kestrel. HTTP.sys можно использовать в сценариях, где приложение имеет доступ к Интернету и необходимые возможности поддерживаются HTTP.sys, но не Kestrel.

Kestrel не имеет эквивалента модулям IIS (хотя приложения, размещенные в IIS, по-прежнему могут использовать преимущества модулей IIS). Для достижения эквивалентного поведения обычно используется [промежуточный](/aspnet/core/fundamentals/middleware/) слой, настроенный в самом приложении ASP.NET Core.

## <a name="references"></a>Ссылки

- [Модули IIS](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [ПО промежуточного слоя ASP.NET Core](/aspnet/core/fundamentals/middleware/)
- [Серверы ASP.NET Core](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
>[Назад](app-startup-differences.md)
>[Вперед](serving-static-files.md)
