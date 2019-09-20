---
title: IServerVirtualDeviceSet2::BeginConfiguration
titlesuffix: SQL Server VDI reference
description: Dieser Artikel enthält Referenzinformationen zum IServerVirtualDeviceSet2::BeginConfiguration-Befehl.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fea109e55b9efa5619bdccb11d692ffebd1a6847
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847481"
---
# <a name="iservervirtualdeviceset2beginconfiguration-vdi"></a>IServerVirtualDeviceSet2::BeginConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Der Server ruft die **beginconfiguration**-Funktion auf, um die Konfiguration der Gruppe virtueller Geräte zu starten.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::BeginConfiguration (
   DWORD   dwFeatures,
   DWORD   dwAlignment,
   DWORD   dwBlockSize,
   DWORD   dwMaxTransferSize,
   DWORD   dwTimeout
);
```

## <a name="parameters"></a>Parameter

*dwfeatures*: Die geänderte Featuremaske. VDF_WriteMedia und/oder VDF_ReadMedia.

*dwalignment*: Die endgültige Ausrichtung. Wenn der Wert 0 ist, entspricht er standardmäßig „dwblocksize“. Muss eine Potenz von 2, > = dwblocksize und < = 64 KB sein.

*dwblocksize*: Die kleinste Übertragungseinheit in Bytes. Muss eine Potenz von 2, > = 512 und < = 64 KB sein.

*dwmaxtransfersize*: Die größte Übertragung, die versucht wird. Muss ein Vielfaches von 64 KB sein.

*dwtimeout*: Wartezeit in Millisekunden. bis der primäre Client das Deklarieren von Pufferbereichen, die er bereitstellt, abgeschlossen hat.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Die Gruppe virtueller Geräte befindet sich im konfigurierbaren Zustand. |
| VD_E_ABORT | „SignalAbort“ wurde aufgerufen. |
| VD_E_PROTOCOL | Die Gruppe virtueller Geräte befindet sich nicht im verbundenen Zustand. |

## <a name="remarks"></a>Remarks

Nach Aufrufen dieser Funktion wechselt die Gruppe der virtuellen Geräte in den konfigurierbaren Zustand, in dem das Pufferlayout festgelegt wird.
Nach Festlegen der Basiskonfiguration (gemäß den Parametern) bleiben diese Werte für die Lebensdauer der Gruppe der virtuellen Geräte unverändert. Die Eigenschaft „Ausrichtung“ der Gruppe virtueller Geräte wird verwendet, um die Ausrichtung von Datenpuffern zu steuern. Dieser Wert legt einen minimalen Ausrichtungswert fest, der auf Puffer-für-Puffer-Basis überschrieben werden kann.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).