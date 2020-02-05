---
title: IClientVirtualDeviceSet2::Close
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDeviceSet2::Close“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5f87b375773b9c81b29b3b5cac11ea97121c45df
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847381"
---
# <a name="iclientvirtualdeviceset2close-vdi"></a>IClientVirtualDeviceSet2::Close (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die **Close**-Funktion schließt die Gruppe virtueller Geräte, die durch „IClientVirtualDeviceSet2::Create“ erstellt wurde. Dadurch werden alle Ressourcen freigegeben, die der Gruppe virtueller Geräte zugeordnet sind.

## <a name="syntax"></a>Syntax

```c
HRESULT IClientVirtualDeviceSet2::Close ();
```

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Dieses Argument wird zurückgegeben, wenn die Gruppe virtueller Geräte erfolgreich geschlossen wurde. |
| VD_E_PROTOCOL | Es wurde keine Aktion ausgeführt, weil die Gruppe virtueller Geräte nicht geöffnet war. |
| VD_E_OPEN | Die Geräte waren noch geöffnet. |

## <a name="remarks"></a>Bemerkungen

Wenn der Client „Close“ aufruft, wird damit darauf hingewiesen, dass alle Ressourcen, die von der Gruppe virtueller Geräte genutzt werden, freigegeben werden sollten. Der Client muss sicherstellen, dass alle Aktivitäten, die Datenpuffer und virtuelle Geräte betreffen, vor dem Aufrufen von „Close“ beendet werden. Dies liegt daran, dass durch „Close“ sämtliche von „OpenDevice“ zurückgegebene Schnittstellen virtueller Geräte ungültig werden.

Nach der Rückgabe des „Close“-Aufrufs hat der Client die Möglichkeit, einen „Create“-Aufruf an die Schnittstelle für die Gruppe virtueller Geräte zu senden. Durch einen solchen Aufruf wird eine Gruppe virtueller Geräte für einen nachfolgenden BACKUP- oder RESTORE-Vorgang erstellt.

Wenn „Close“ aufgerufen wird und noch mindestens ein virtuelles Gerät geöffnet ist, wird VD_E_OPEN zurückgegeben. In diesem Fall wird „SignalAbort“ intern ausgelöst, um nach Möglichkeit ein ordnungsgemäßes Herunterfahren zu gewährleisten. Dabei werden VDI-Ressourcen freigegeben. Der Client sollte auf jedem Gerät warten, bis die Angabe „VD_E_CLOSE“ übermittelt wird. Erst danach sollte er „IClientVirtualDeviceSet2::Close“ aufrufen. Wenn dem Client bekannt ist, dass sich die Gruppe virtueller Geräte bereits im Zustand der unplanmäßigen Beendigung befindet, sollte der Client nicht annehmen, dass die Angabe „VD_E_CLOSE“ von „GetCommand“ übermittelt wird. Der Client hat die Möglichkeit, „IClientVirtualDeviceSet2::Close“ aufzurufen, sobald die Aktivität im Zusammenhang mit den gemeinsam verwendeten Puffern beendet wird.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).