---
title: Aktualisieren von Daten in SQL Server-Cursorn
description: Aktualisieren von Daten in SQL Server-Cursorn
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b9351b2fd5000e2d93ed2c66446a16b8dc718c0c
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107712"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aktualisieren von Daten in SQL Server-Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Beim Abrufen und Aktualisieren von Daten mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursorn gelten für die Consumeranwendung eines OLE DB-Treibers für SQL Server die gleichen Überlegungen und Einschränkungen wie für jede andere Clientanwendung.  
  
 Nur Zeilen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursorn nehmen an der gleichzeitigen Datenzugriffssteuerung teil. Wenn der Consumer ein änderbares Rowset anfordert, wird die Parallelitätssteuerung von DBPROP_LOCKMODE kontrolliert. Um die Steuerungsebene für den gleichzeitigen Zugriff zu ändern, legt der Consumer die DBPROP_LOCKMODE-Eigenschaft vor dem Öffnen des Rowsets fest.  
  
 Transaktionsisolationsstufen können zu beträchtlichen Verzögerungen bei der Zeilenpositionierung führen, wenn Transaktionen aufgrund des Designs der Clientanwendung über längere Zeit geöffnet bleiben. Standardmäßig verwendet der OLE DB-Treiber für SQL Server die von DBPROPVAL_TI_READCOMMITTED angegebene READ COMMITTED-Isolationsstufe. Der  Native Client OLE DB-Anbieter unterstützt die Dirty Read-Isolation, wenn die Rowsetparallelität schreibgeschützt ist. Daher kann der Consumer in einem änderbaren Rowset eine höhere Isolationsstufe jedoch keine niedrigere Stufe erfolgreich anfordern.  
  
## <a name="immediate-and-delayed-update-modes"></a>Unmittelbarer und verzögerter Updatemodus  
 Im Sofortupdatemodus verursacht jeder Aufruf von **IRowsetChange::SetData** einen Roundtrip zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Wenn der Consumer mehrere Änderungen an einer einzelnen Zeile vornimmt, ist es effizienter, alle Änderungen mit einem einzigen **SetData**-Aufruf zu übergeben.  
  
 Im verzögerten Updatemodus wird für jede im *cRows*-Parameter und *rghRows*-Parameter von **IRowsetUpdate::Update** angegebene Zeile ein Roundtrip zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] durchgeführt.  
  
 In beiden Modi stellt ein Roundtrip eine separate Transaktion dar, wenn kein Transaktionsobjekt für das Rowset geöffnet ist.  
  
 Wenn Sie IRowsetUpdate::Update**verwenden, versucht der** Native Client OLE DB-Anbieter jede angegebene Zeile zu verarbeiten. Die Verarbeitung durch den OLE DB-Treiber für SQL Server wird durch einen Fehler aufgrund ungültiger Daten-, Längen- oder Statuswerte einer Zeile nicht angehalten. Es können nur alle oder keine der anderen am Update beteiligten Zeilen geändert werden. Der Consumer muss das zurückgegebene *prgRowStatus*-Array untersuchen, um bestimmte Zeilen auf Fehler zu überprüfen, wenn der OLE DB-Treiber für SQL Server DB_S_ERRORSOCCURRED zurückgibt.  
  
 Ein Consumer darf nicht davon ausgehen, dass Zeilen in einer bestimmten Reihenfolge verarbeitet werden. Wenn ein Consumer es erfordert, dass die Verarbeitung von Datenänderungen in mehr als einer Zeile in einer bestimmten Reihenfolge durchgeführt wird, muss der Consumer diese Reihenfolge in der Anwendungslogik festlegen und eine Transaktion öffnen, um den Prozess darin einzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Aktualisieren von Daten in Rowsets](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
