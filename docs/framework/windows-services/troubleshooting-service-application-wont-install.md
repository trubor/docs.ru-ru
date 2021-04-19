---
title: 'Устранение неполадок: невозможно установить приложение-службу'
description: Устраните неполадки, если невозможно установить приложение-службу. Убедитесь, что свойству ServiceName для класса службы задано правильное значение.
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
ms.openlocfilehash: 057fe52d43daad90df862c3acaec41a427333cba
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494432"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="56b4c-104">Устранение неполадок: невозможно установить приложение-службу</span><span class="sxs-lookup"><span data-stu-id="56b4c-104">Troubleshooting: Service Application Won't Install</span></span>

<span data-ttu-id="56b4c-105">Если приложение-служба не устанавливается надлежащим образом, убедитесь, что для свойства <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> класса службы задано значение, которое отображается в установщике этой службы.</span><span class="sxs-lookup"><span data-stu-id="56b4c-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="56b4c-106">Для правильной установки службы необходимо, чтобы эти значения совпадали.</span><span class="sxs-lookup"><span data-stu-id="56b4c-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56b4c-107">Сведения о ходе установки также можно найти в журналах установки.</span><span class="sxs-lookup"><span data-stu-id="56b4c-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="56b4c-108">Также убедитесь, что у вас не установлена другая служба с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="56b4c-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="56b4c-109">Для успешной установки необходимо, чтобы у каждой службы было уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="56b4c-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b4c-110">См. также</span><span class="sxs-lookup"><span data-stu-id="56b4c-110">See also</span></span>

- [<span data-ttu-id="56b4c-111">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="56b4c-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
