---
title: IClientVirtualDeviceSet2::MapBufferHandle
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDeviceSet2::MapBufferHandle“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5d181d1b6ddfea034716ebb048768cd7d43fbc61
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847581"
---
# <a name="iclientvirtualdeviceset2mapbufferhandle-vdi"></a>IClientVirtualDeviceSet2::MapBufferHandle (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit der Funktion **MapBufferHandle** wird eine gültige Pufferadresse aus einem Pufferhandle abgerufen, das wiederum aus einem anderen Prozess abgerufen wurde.

## <a name="syntax"></a>Syntax

```c
HRESULT IClientVirtualDeviceSet2::MapBufferHandle (
   DWORD      dwBuffer,
   BYTE**      ppBuffer
);
```

## <a name="parameters"></a>Parameter

*dwBuffer*: Handle, das von „IClientVirtualDeviceSet2::GetBufferHandle“ zurückgegeben wird.

*ppBuffer*: Adresse des Puffers, der im aktuellen Prozess gültig ist.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Die Funktion wurde erfolgreich ausgeführt. |
| VD_E_PROTOCOL | Die Gruppe virtueller Geräte ist aktuell nicht geöffnet. |
| VD_E_INVALID | „ppBuffer“ ist ein ungültiges Handle. |

## <a name="remarks"></a>Remarks

Die Handles müssen unbedingt korrekt übermittelt werden. da sie für eine einzelne Gruppe virtueller Geräte nur lokal verfügbar sind. Die Partnerprozesse, die ein Handle gemeinsam nutzen, müssen sicherstellen, dass Pufferhandles nur innerhalb des Bereichs der Gruppe virtueller Geräte verwendet werden, aus dem der Puffer ursprünglich abgerufen wurde.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).