---
title: IServerVirtualDeviceSet2::IsSharedBuffer
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::IsSharedBuffer“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cd3e7abfd1d250a170e0de4ebc1b392bc5857468
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847361"
---
# <a name="iservervirtualdeviceset2issharedbuffer-vdi"></a>IServerVirtualDeviceSet2::IsSharedBuffer (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit der Funktion **IsSharedBuffer** wird festgelegt, ob die vorhandene Pufferadresse auf einen der freigegebenen Puffer verweist, die von der Methode „AllocateBuffer“ bereitgestellt wurden.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::IsSharedBuffer (
   LPVOID   lpBuffer
);
```

## <a name="parameters"></a>Parameter

*lpBuffer*: Die Adresse eines Puffers.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| TRUE | Der Puffer ist freigegeben. |
| FALSE | Der Puffer ist nicht Teil der Gruppe virtueller Geräte. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).