---
title: IServerVirtualDeviceSet2::EndConfiguration
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::EndConfiguration“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5060a862f61f005c83296235bcef5a2851bcaeca
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847301"
---
# <a name="iservervirtualdeviceset2endconfiguration-vdi"></a>IServerVirtualDeviceSet2::EndConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit der Funktion **EndConfiguration** wird die VDI darüber informiert, dass der Server die Konfiguration beendet hat.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::EndConfiguration ();
```

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Die Funktion wurde erfolgreich ausgeführt. |
| VD_E_ABORT | Ein Abbruch wurde angefordert. |
| VD_E_PROTOCOL | Die Gruppe befindet sich nicht im Zustand „Konfigurierbar“. |
| VD_E_MEMORY | Der über die RequestBuffers-Aufrufe angeforderte Arbeitsspeicher konnte nicht abgerufen werden. Die Gruppe bleibt im Zustand „Konfigurierbar“ ohne verfügbaren Pufferspeicher. Der Server kann entweder die Pufferanforderungen reduzieren oder den Vorgang abbrechen. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).