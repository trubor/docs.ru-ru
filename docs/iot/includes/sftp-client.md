---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594020"
---
<span data-ttu-id="32701-101">[С помощью клиента SFTP](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md) скопируйте файлы из расположения публикации на компьютере разработчика в новую папку на устройстве Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="32701-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="32701-102">Например, чтобы использовать команду `scp` для копирования файлов с компьютера разработчика на устройство Raspberry Pi, откройте командную строку и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="32701-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="32701-103">Где:</span><span class="sxs-lookup"><span data-stu-id="32701-103">Where:</span></span>

- <span data-ttu-id="32701-104">Параметр `-r` предписывает `scp` рекурсивно копировать файлы.</span><span class="sxs-lookup"><span data-stu-id="32701-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="32701-105">*/publish-location/* — это папка, опубликованная на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="32701-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="32701-106">`pi@raspberypi` — имя пользователя и узла в формате `<username>@<hostname>`.</span><span class="sxs-lookup"><span data-stu-id="32701-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="32701-107">*/home/pi/deployment-location/* — это новая папка на Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="32701-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="32701-108">Последние версии Windows поставляются с OpenSSH, включая `scp`.</span><span class="sxs-lookup"><span data-stu-id="32701-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>
