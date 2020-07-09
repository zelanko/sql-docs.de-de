---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDeviceSet2::GetConfiguration“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 52dcbd2e2218da289d447b16d29460ff3f5af977
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896887"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Die Funktion **GetConfiguration** wird verwendet, um solange zu warten, bis der Server die Gruppe virtueller Geräte konfiguriert hat.

## <a name="syntax"></a>Syntax

```c
HRESULT IClientVirtualDeviceSet2::GetConfiguration (
   DWORD         dwTimeOut,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Parameter

*DwTimeOut*: Timeout in Millisekunden. Verwenden Sie INFINITE, um ein Timeout zu vermeiden.

*pCfg*: Enthält nach erfolgreicher Ausführung die vom Server ausgewählte Konfiguration. Weitere Informationen finden Sie unter „Konfiguration“.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Die Konfiguration wurde zurückgegeben. |
| VD_E_ABORT | „SignalAbort“ wurde aufgerufen. |
| VD_E_TIMEOUT | Bei der Funktionsausführung ist ein Timeout aufgetreten. |

## <a name="remarks"></a>Bemerkungen

Diese Funktion wird im Warnzustand blockiert. Nach dem erfolgreichen Aufruf können die Geräte in der Gruppe virtueller Geräte geöffnet werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).