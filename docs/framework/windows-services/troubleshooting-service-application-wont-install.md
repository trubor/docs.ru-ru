---
title: 'Устранение неполадок: невозможно установить приложение-службу'
description: Устраните неполадки, если невозможно установить приложение-службу. Убедитесь, что свойству ServiceName для класса службы задано правильное значение.
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
ms.openlocfilehash: 02ac95c22007caa6e30300fb8a98178f11cecd14
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270358"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="c8c9a-104">Устранение неполадок: невозможно установить приложение-службу</span><span class="sxs-lookup"><span data-stu-id="c8c9a-104">Troubleshooting: Service Application Won't Install</span></span>

<span data-ttu-id="c8c9a-105">Если приложение-служба не устанавливается надлежащим образом, убедитесь, что для свойства <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> класса службы задано значение, которое отображается в установщике этой службы.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="c8c9a-106">Для правильной установки службы необходимо, чтобы эти значения совпадали.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8c9a-107">Сведения о ходе установки также можно найти в журналах установки.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="c8c9a-108">Также убедитесь, что у вас не установлена другая служба с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="c8c9a-109">Для успешной установки необходимо, чтобы у каждой службы было уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c9a-110">См. также</span><span class="sxs-lookup"><span data-stu-id="c8c9a-110">See also</span></span>

- [<span data-ttu-id="c8c9a-111">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="c8c9a-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
