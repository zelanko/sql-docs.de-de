---
title: IServerVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::SignalAbort“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee70ef059e80d9c8a31281ce50f451e7787f637a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895944"
---
# <a name="iservervirtualdeviceset2signalabort-vdi"></a>IServerVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Mit der Funktion **SignalAbort** wird angegeben, dass ein Vorgang unplanmäßig beendet werden soll.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Rückgabewert

Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert „NOERROR“ gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.

## <a name="remarks"></a>Bemerkungen

Der Server kann jederzeit den BACKUP- oder RESTORE-Vorgang abbrechen.

Mit dieser Routine wird angegeben, dass alle Vorgänge beendet werden sollen. Die allgemeine Schnittstelle wechselt in den „Abbrechen“-Zustand. Von Geräten werden keine weiteren Befehle angenommen. Der Vervollständigungs-Agent gibt „ERROR_OPERATION_ABORTED“ für jede ausstehende Anforderung zurück und kehrt zum Aufrufer zurück. Alle auf dem Client aufgezeichneten Vervollständigungen werden ignoriert.

Der Server stellt sicher, dass die von der Schnittstelle für virtuelle Geräte zurückgegebenen Puffer oder Geräte nicht mehr benötigt werden. Der Server führt dann einen Cleanup von unplanmäßigen Beendigungen durch, das das Aufrufen der Funktion „IServerVirtualDeviceSet2:: Close“ einschließen sollte.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).