---
title: IServerVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::GetConfiguration“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1d62a2042221bebf04e19a46a21ba81caa7c877b
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847251"
---
# <a name="iservervirtualdeviceset2getconfiguration-vdi"></a>IServerVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Funktion **GetConfiguration** ruft die vom Client angeforderte Konfiguration ab.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::GetConfiguration (
   VDConfig*   pCfg
);
```

## <a name="parameters"></a>Parameter

*pCfg*: Konfiguration, die vom Client mithilfe von „IClientVirtualDeviceSet2::Create“ angegeben wird.

## <a name="return-value"></a>Rückgabewert

Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert „NOERROR“ gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.

## <a name="remarks"></a>Remarks

Der Server soll die vom Client bereitgestellten Einstellungen überprüfen und darauf reagieren. Weitere Informationen finden Sie unter „Konfiguration“. Der Server kann „SignalAbort“ verwenden, wenn er feststellt, dass ein ordnungsgemäßes Arbeiten mit der bereitgestellten Konfiguration nicht möglich ist.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).