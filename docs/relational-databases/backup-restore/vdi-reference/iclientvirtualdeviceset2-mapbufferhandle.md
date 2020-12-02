---
title: IClientVirtualDeviceSet2::MapBufferHandle
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDeviceSet2::MapBufferHandle“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 70f6d117fd7a0349f2da2e03ff2603eaf55898fe
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128959"
---
# <a name="iclientvirtualdeviceset2mapbufferhandle-vdi"></a>IClientVirtualDeviceSet2::MapBufferHandle (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

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

## <a name="remarks"></a>Bemerkungen

Die Handles müssen unbedingt korrekt übermittelt werden. da sie für eine einzelne Gruppe virtueller Geräte nur lokal verfügbar sind. Die Partnerprozesse, die ein Handle gemeinsam nutzen, müssen sicherstellen, dass Pufferhandles nur innerhalb des Bereichs der Gruppe virtueller Geräte verwendet werden, aus dem der Puffer ursprünglich abgerufen wurde.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).