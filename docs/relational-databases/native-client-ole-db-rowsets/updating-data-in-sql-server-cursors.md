---
title: Aktualisieren von Daten in SQL Server Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: befedbeedfad8fcdb7f542d23a7dd1a3854d700f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788793"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aktualisieren von Daten in SQL Server-Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Beim Abrufen und Aktualisieren von Daten mittels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursorn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die Consumeranwendung eines Native Client OLE DB Anbieters durch die gleichen Überlegungen und Einschränkungen gebunden, die für jede andere Client Anwendung gelten.  
  
 Nur Zeilen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursorn nehmen an der gleichzeitigen Datenzugriffssteuerung teil. Wenn der Consumer ein änderbares Rowset anfordert, wird die Parallelitätssteuerung von DBPROP_LOCKMODE kontrolliert. Um die Steuerungsebene für den gleichzeitigen Zugriff zu ändern, legt der Consumer die DBPROP_LOCKMODE-Eigenschaft vor dem Öffnen des Rowsets fest.  
  
 Transaktionsisolationsstufen können zu beträchtlichen Verzögerungen bei der Zeilenpositionierung führen, wenn Transaktionen aufgrund des Designs der Clientanwendung über längere Zeit geöffnet bleiben. Standardmäßig verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieter die durch DBPROPVAL_TI_READCOMMITTED angegebene Isolationsstufe mit Leseberechtigung. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Dirty Read Isolation, wenn die Rowsetparallelität schreibgeschützt ist. Daher kann der Consumer in einem änderbaren Rowset eine höhere Isolationsstufe jedoch keine niedrigere Stufe erfolgreich anfordern.  
  
## <a name="immediate-and-delayed-update-modes"></a>Unmittelbarer und verzögerter Updatemodus  
 Im Sofortupdatemodus verursacht jeder Aufruf von **IRowsetChange::SetData** einen Roundtrip zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn der Consumer mehrere Änderungen an einer einzelnen Zeile vornimmt, ist es effizienter, alle Änderungen mit einem einzigen **SetData**-Aufruf zu übergeben.  
  
 Im verzögerten Updatemodus wird für jede im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]cRows *-Parameter und *rghRows *-Parameter von *IRowsetUpdate::Update** angegebene Zeile ein Roundtrip zu ** durchgeführt.  
  
 In beiden Modi stellt ein Roundtrip eine separate Transaktion dar, wenn kein Transaktionsobjekt für das Rowset geöffnet ist.  
  
 Wenn Sie **IRowsetUpdate:: Update**verwenden, versucht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, jede bestimmte Zeile zu verarbeiten. Aufgrund ungültiger Daten-, Längen-oder Statuswerte für eine Zeile wird die Verarbeitung von Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB-Anbietern nicht beendet. Es können nur alle oder keine der anderen am Update beteiligten Zeilen geändert werden. Der Consumer muss das zurückgegebene *prgRowStatus* -Array untersuchen, um den Fehler für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmte Zeile zu ermitteln, wenn der Native Client OLE DB-Anbieter DB_S_ERRORSOCCURRED zurückgibt.  
  
 Ein Consumer darf nicht davon ausgehen, dass Zeilen in einer bestimmten Reihenfolge verarbeitet werden. Wenn ein Consumer es erfordert, dass die Verarbeitung von Datenänderungen in mehr als einer Zeile in einer bestimmten Reihenfolge durchgeführt wird, muss der Consumer diese Reihenfolge in der Anwendungslogik festlegen und eine Transaktion öffnen, um den Prozess darin einzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
