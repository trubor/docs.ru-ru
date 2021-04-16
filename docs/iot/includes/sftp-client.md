---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594020"
---
[С помощью клиента SFTP](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md) скопируйте файлы из расположения публикации на компьютере разработчика в новую папку на устройстве Raspberry Pi.

Например, чтобы использовать команду `scp` для копирования файлов с компьютера разработчика на устройство Raspberry Pi, откройте командную строку и выполните следующую команду:

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

Где:

- Параметр `-r` предписывает `scp` рекурсивно копировать файлы.
- */publish-location/* — это папка, опубликованная на предыдущем шаге.
- `pi@raspberypi` — имя пользователя и узла в формате `<username>@<hostname>`.
- */home/pi/deployment-location/* — это новая папка на Raspberry Pi.

> [!TIP]
> Последние версии Windows поставляются с OpenSSH, включая `scp`.
