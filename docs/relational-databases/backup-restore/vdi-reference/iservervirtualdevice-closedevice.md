---
title: IServerVirtualDevice::CloseDevice
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDevice::CloseDevice“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3e9ff54c500b626d667622105a39e742c5e2a339
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896828"
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