---
title: IDBProperties-Schnittstelle (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135870"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Der OLE DB-Standardspezifikation kann Anbieter VT_EMPTY für an `DBPROPINFO::vValues`. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB immer VT_EMPTY zurückgegeben, wenn Sie aufrufen `IDBProperties::GetPropertyInfo` mit `DBPROPSET_ROWSETALL` zum Abrufen von Rowset-Eigenschaften.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
