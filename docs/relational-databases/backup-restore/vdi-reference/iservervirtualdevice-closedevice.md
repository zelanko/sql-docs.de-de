---
title: IServerVirtualDevice::CloseDevice
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDevice::CloseDevice“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 61d877fddb32f6455303a006e8955b1042ce7aa6
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128905"
---
# <a name="iservervirtualdeviceclosedevice-vdi"></a>IServerVirtualDevice::CloseDevice (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Mit der Funktion **CloseDevice** wird ein virtuelles Gerät geschlossen, das mit „IServerVirtualDeviceSet2::OpenDevice“ geöffnet wurde.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDevice::CloseDevice ();
```

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| VD_E_CLOSE | Das Gerät ist bereits geschlossen. |
| VD_E_ABORT | Die Schnittstelle befindet sich im Zustand „Abbruch“. |

## <a name="remarks"></a>Bemerkungen

Wurde „SignalAbort“ zum Erzwingen einer unplanmäßigen Beendigung verwendet, ist die Verwendung von „CloseDevice“ nicht mehr erforderlich. Wenn „CloseDevice“ nach der Verwendung von „SignalAbort“ aufgerufen wird, wird keine Aktion ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).