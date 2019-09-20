---
title: IServerVirtualDevice::SendCommand
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDevice::SendCommand“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c75cd206557547f55d47eec0a7aec52cc0069b71
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847511"
---
# <a name="iservervirtualdevicesendcommand-vdi"></a>IServerVirtualDevice::SendCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die **SendCommand**-Funktion sendet mithilfe eines von „IServerVirtualDeviceSet2::OpenDevice“ zurückgegebenen virtuellen Geräteobjekts einen Befehl an den Client.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDevice::SendCommand (
   VDS_Command*   pCmd
);
```

## <a name="parameters"></a>Parameter

*pCmd*: Ein Zeiger auf einen Befehlsanforderungsblock. Weitere Informationen finden Sie im Abschnitt zu den Befehlen. Das Feld „completionFunction“ muss so festgelegt werden, dass es auf die Adresse einer Funktion mit der folgenden Signatur verweist:

```c
void callbackFunction ( VDS_Command *pCmd);
```

Dieser Rückruf erfolgt durch den Vervollständigungs-Agent, wenn der Client anzeigt, dass ein Befehl vervollständigt wurde. SQL Server legt das Feld „completionContext“ von „pCmd“ fest. Der Zweck besteht darin, den Kontext für die Rückruffunktion bereitzustellen.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Der Befehl wurde erfolgreich in die Warteschlange für den Client gestellt. |
| VD_E_QUEUE_FULL | Die Gerätewarteschlange ist voll. |
| VD_E_IO_ERROR | Das Gerät befindet sich in einem IO-ERROR-Zustand. |
| VD_E_PROTOCOL | Das Gerät ist nicht aktiv. |

## <a name="remarks"></a>Remarks

Wenn beim Versuch, den Befehl zu senden, ein Fehler auftritt, wird die Rückruffunktion aufgerufen, und „completionCode“ im Befehlspuffer wird wie folgt festgelegt:

| completionCode | Fehler |
|---|---|
| VD_E_QUEUE_FULL | ERROR_NO_SYSTEM_RESOURCES |
| VD_E_IO_ERROR   | ERROR_IO_DEVICE |
| VD_E_PROTOCOL   | ERROR_INVALID_HANDLE |
| VD_E_ABORT      | ERROR_OPERATION_ABORTED |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).