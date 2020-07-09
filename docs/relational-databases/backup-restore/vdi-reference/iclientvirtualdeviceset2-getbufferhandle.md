---
title: IClientVirtualDeviceSet2::GetBufferHandle
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IClientVirtualDeviceSet2::GetBufferHandle“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cf187379aaa664e536710859e08bf084b14657d1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896905"
---
# <a name="iclientvirtualdeviceset2getbufferhandle-vdi"></a>IClientVirtualDeviceSet2::GetBufferHandle (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Für einige Anwendungen sind möglicherweise mehrere Prozesse erforderlich, damit Puffer verarbeitet werden können, die von **IClientVirtualDevice2::GetCommand** zurückgegeben werden. In solchen Fällen kann der Prozess, der den Befehl empfängt, mithilfe von **GetBufferHandle** ein prozessunabhängiges Handle abrufen, das den Puffer identifiziert. Dieses Handle kann dann jedem Prozess übergeben werden, für den dieselbe Gruppe virtueller Geräte geöffnet ist. Anschließend kann der Prozess mit „IClientVirtualDeviceSet2::MapBufferHandle“ die Adresse des Puffers abrufen. Bei der Adresse handelt es sich wahrscheinlich um eine andere Adresse als die im zugehörigen Partnerprozess, da jeder Prozess verschiedene Adressen verwenden kann, um Puffer zuzuordnen.

## <a name="syntax"></a>Syntax

```c
HRESULT IClientVirtualDeviceSet2::GetBufferHandle (
   BYTE*         pBuffer,
   DWORD*      pBufferHandle
);
```

## <a name="parameters"></a>Parameter

*pBuffer*: Adresse eines Puffers, der von einem Lese- oder Schreibbefehl abgerufen wird.

*pBufferHandle*: Ein eindeutiger Bezeichner für den Puffer wird zurückgegeben.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Die Funktion wurde erfolgreich ausgeführt. |
| VD_E_PROTOCOL | Die Gruppe virtueller Geräte ist aktuell nicht geöffnet. |
| VD_E_INVALID | „pBuffer“ ist keine gültige Adresse. |

## <a name="remarks"></a>Bemerkungen

Der Prozess, der die Funktion „GetBufferHandle“ aufruft, ist auch für den Aufruf von „IClientVirtualDevice2::CompleteCommand“ verantwortlich, nachdem die Datenübertragung abgeschlossen wurde.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).