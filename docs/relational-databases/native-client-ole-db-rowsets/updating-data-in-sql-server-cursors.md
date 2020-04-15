---
title: Aktualisieren von Daten in SQL Server-Cursorn | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 788055ec21a215a99b2524310452d14ba390088a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300244"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aktualisieren von Daten in SQL Server-Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Beim Abrufen und Aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über Cursor ist eine Consumeranwendung des nativen Client-OLE-DB-Anbieters an dieselben Überlegungen und Einschränkungen gebunden, die für jede andere Clientanwendung gelten.  
  
 Nur Zeilen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursorn nehmen an der gleichzeitigen Datenzugriffssteuerung teil. Wenn der Consumer ein änderbares Rowset anfordert, wird die Parallelitätssteuerung von DBPROP_LOCKMODE kontrolliert. Um die Steuerungsebene für den gleichzeitigen Zugriff zu ändern, legt der Consumer die DBPROP_LOCKMODE-Eigenschaft vor dem Öffnen des Rowsets fest.  
  
 Transaktionsisolationsstufen können zu beträchtlichen Verzögerungen bei der Zeilenpositionierung führen, wenn Transaktionen aufgrund des Designs der Clientanwendung über längere Zeit geöffnet bleiben. Standardmäßig verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der native Client-OLE-DB-Anbieter die von DBPROPVAL_TI_READCOMMITTED angegebene Isolationsstufe für Lesefestier. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt die schmutzige Leseisolation, wenn die Rowset-Parallelität schreibgeschützt ist. Daher kann der Consumer in einem änderbaren Rowset eine höhere Isolationsstufe jedoch keine niedrigere Stufe erfolgreich anfordern.  
  
## <a name="immediate-and-delayed-update-modes"></a>Unmittelbarer und verzögerter Updatemodus  
 Im Sofortupdatemodus verursacht jeder Aufruf von **IRowsetChange::SetData** einen Roundtrip zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn der Consumer mehrere Änderungen an einer einzelnen Zeile vornimmt, ist es effizienter, alle Änderungen mit einem einzigen **SetData**-Aufruf zu übergeben.  
  
 Im verzögerten Updatemodus wird für jede im *cRows*-Parameter und *rghRows*-Parameter von **IRowsetUpdate::Update** angegebene Zeile ein Roundtrip zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchgeführt.  
  
 In beiden Modi stellt ein Roundtrip eine separate Transaktion dar, wenn kein Transaktionsobjekt für das Rowset geöffnet ist.  
  
 Wenn Sie **IRowsetUpdate::Update**verwenden, versucht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter, jede angegebene Zeile zu verarbeiten. Ein Fehler, der aufgrund ungültiger Daten-, Längen- oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Statuswerte für eine Zeile auftritt, stoppt die Verarbeitung des Native Client OLE DB-Anbieters nicht. Es können nur alle oder keine der anderen am Update beteiligten Zeilen geändert werden. Der Consumer muss das zurückgegebene *prgRowStatus-Array* untersuchen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um einen Fehler für eine bestimmte Zeile zu ermitteln, wenn der native Client-OLE-DB-Anbieter DB_S_ERRORSOCCURRED zurückgibt.  
  
 Ein Consumer darf nicht davon ausgehen, dass Zeilen in einer bestimmten Reihenfolge verarbeitet werden. Wenn ein Consumer es erfordert, dass die Verarbeitung von Datenänderungen in mehr als einer Zeile in einer bestimmten Reihenfolge durchgeführt wird, muss der Consumer diese Reihenfolge in der Anwendungslogik festlegen und eine Transaktion öffnen, um den Prozess darin einzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Daten in Rowsets](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
