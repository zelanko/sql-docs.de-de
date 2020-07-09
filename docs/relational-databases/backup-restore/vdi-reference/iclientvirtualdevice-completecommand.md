---
title: IClientVirtualDevice::CompleteCommand
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDevice::CompleteCommand“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dda70978e4daba50018b58c3cf9aeaaaa4374551
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896945"
---
# <a name="iclientvirtualdevicecompletecommand-vdi"></a>IClientVirtualDevice::CompleteCommand (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Mit der Funktion **CompleteCommand** wird SQL Server benachrichtigt, dass ein Befehl abgeschlossen wurde. Für den Befehl sollten geeignete Abschlussinformationen zurückgegeben werden.

## <a name="syntax"></a>Syntax

```c
HRESULT IClientVirtualDevice::CompleteCommand (
   VDC_Command*         const pCmd,
   UINT32               dwCompletionCode,
   UINT32               dwBytesTransferred,
   UINT64               dwlPosition
);
```

## <a name="parameters"></a>Parameter

*pCmd*: Gibt die Adresse eines Befehls an, der zuvor von „IClientVirtualDevice::GetCommand“ zurückgegeben wurde.

*dwCompletionCode*: Gibt einen WIN32-Statuscode an, der auf den Abschlussstatus hinweist. Dieser Parameter muss für alle Befehle zurückgegeben werden. Der zurückgegebene Code sollte für den Befehl geeignet sein, der ausgeführt wird. ERROR_SUCCESS wird immer verwendet, um einen erfolgreich ausgeführten Befehl anzugeben. Eine vollständige Liste der möglichen Codes finden Sie in der Datei „Winerror.h“. Eine Liste der typischen Statuscodes für jeden Befehl finden Sie unter „Befehle“.

*dwBytesTransferred*: Gibt die Anzahl der erfolgreich übertragenen Bytes an. Dieses Argument wird nur für Lese-und Schreibvorgänge zurückgegeben, die Datenübertragungsbefehle betreffen.

*dwlPosition*: Gibt eine Antwort ausschließlich für den Befehl „GetPosition“ an.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Der Abschluss wurde korrekt erfasst. |
| VD_E_INVALID | „pCmd“ war kein aktiver Befehl. |
| VD_E_ABORT | Ein Abbruch wurde gemeldet. |
| VD_E_PROTOCOL | Das Gerät ist nicht geöffnet. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).
