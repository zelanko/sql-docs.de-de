---
title: IDBProperties (OLE DB) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62692183"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für `DBPROPINFO::vValues` angeben. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt Native Client OLE DB immer VT_EMPTY zurück, wenn `IDBProperties::GetPropertyInfo` Sie `DBPROPSET_ROWSETALL` mit aufrufen, um Rowseteigenschaften abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
