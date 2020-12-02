---
title: IServerVirtualDeviceSet2::Close
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::Close“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 10e699462f2e0b01cb5973e3aeb033ffe10e7680
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128928"
---
# <a name="iservervirtualdeviceset2close-vdi"></a>IServerVirtualDeviceSet2::Close (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Die Funktion **Close** schließt die von „IServerVirtualDeviceSet2::Open“ geöffneten virtuellen Geräte. Dadurch werden alle Ressourcen freigegeben, die dem virtuellen Gerät zugeordnet sind. Das „IServerVirtualDeviceSet2“-Handle ist nicht nützlich, nachdem diese Funktion zurückgegeben wurde, und sollte an COM zurückgegeben werden.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::Close ();
```

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| VD_E_PROTOCOL | Die Geräte waren noch geöffnet. |

## <a name="remarks"></a>Bemerkungen

Die virtuellen Geräte sollten nicht vor dem Schließen der Geräte geschlossen werden. In diesem Fall wird „VD_E_PROTOCOL“ zurückgegeben. Diese Aktion führt dazu, dass ein sofortiges Schließen erfolgt und dabei die Zuordnung von gemeinsam genutztem Speicherbereich freigegeben wird. Der Server unterliegt Zugriffsverletzungen, wenn er weiterhin mit dem Besitz von Ressourcen rechnet, die von der virtuellen Geräteschnittstelle zurückgegeben werden. Die Schnittstelle führt die SignalAbort-Verarbeitung aus.

Wenn der Vervollständigungs-Agent ausgeführt wird, vervollständigt er alle ausstehenden Befehle, bevor er zum Aufrufer zurückkehrt. Ausstehende Befehle werden mit „ERROR_OPERATION_ABORTED“ abgeschlossen. Das heißt, die Rückruffunktion wird für jeden dieser Befehle aufgerufen.

In allen Fällen, auch dann, wenn Fehler zurückgegeben werden, werden mit „Close“ alle Ressourcen für die Schnittstelle virtueller Geräte freigegeben. Alle Puffer und andere von der VDI zurückgegebenen Schnittstellenzeiger werden ungültig.

Es ist wichtig sicherzustellen, dass der Vervollständigungs-Agent vor dem Entladen der COM-Bibliothek beendet wurde. Wenn die Bibliothek entladen wird, bevor der Vervollständigungs-Agent an den Aufrufer zurückkehrt, kann der Prozess einen Anweisungsverstoß verursachen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).