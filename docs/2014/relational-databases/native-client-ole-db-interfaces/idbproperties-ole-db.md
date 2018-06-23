---
title: IDBProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bee573d18bce37685612ab79a715834ca27e5fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060936"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für an `DBPROPINFO::vValues`. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB immer VT_EMPTY zurückgegeben, wenn Sie aufrufen `IDBProperties::GetPropertyInfo` mit `DBPROPSET_ROWSETALL` Rowseteigenschaften abgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  