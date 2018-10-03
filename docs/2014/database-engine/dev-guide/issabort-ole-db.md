---
title: ISSAbort (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4b3e43dca5a18a991733492eeeffc4f49d14ef8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181240"
---
# <a name="issabort-ole-db"></a>'ISSAbort' (OLE DB)
  Die **ISSAbort** -Schnittstelle, die verfügbar gemacht wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die [issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) -Methode, die verwendet wird, um das aktuelle Rowset sowie Befehle abzubrechen, einem Batch verarbeitet mit dem Befehl, der das Rowset ursprünglich generierte, und, die Ausführung noch nicht abgeschlossen haben.  
  
 **ISSAbort** ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anbieter spezifische Schnittstelle verfügbar, **QueryInterface** auf die **IMultipleResults** zurückgegebenes Objekt  **ICommand:: Execute** oder **IOpenRowset:: OPENROWSET**.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|Description|  
|------------|-----------------|  
|[Issabort:: Abort &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Bricht das aktuelle Rowset sowie eventuell mit dem aktuellen Befehl verknüpfte Batchbefehle ab.|  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
