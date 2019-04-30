---
title: Aktualisieren von Daten in SQL Server-Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: b5c0b188d8fd45c1177cab77501bdf80fc550987
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242920"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aktualisieren von Daten in SQL Server-Cursorn
  Beim Abrufen und Aktualisieren von Daten mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cursorn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer-Anwendung gebunden ist, indem Sie die gleichen Überlegungen und Einschränkungen, die für jede andere Clientanwendung gelten.  
  
 Nur Zeilen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursorn nehmen an der gleichzeitigen Datenzugriffssteuerung teil. Wenn der Consumer ein änderbares Rowset anfordert, wird die Parallelitätssteuerung von DBPROP_LOCKMODE kontrolliert. Um die Steuerungsebene für den gleichzeitigen Zugriff zu ändern, legt der Consumer die DBPROP_LOCKMODE-Eigenschaft vor dem Öffnen des Rowsets fest.  
  
 Transaktionsisolationsstufen können zu beträchtlichen Verzögerungen bei der Zeilenpositionierung führen, wenn Transaktionen aufgrund des Designs der Clientanwendung über längere Zeit geöffnet bleiben. In der Standardeinstellung die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet, die von DBPROPVAL_TI_READCOMMITTED angegebene Read committed-Isolationsstufe. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die dirty read-Isolation, wenn die rowsetparallelität schreibgeschützt ist. Daher kann der Consumer in einem änderbaren Rowset eine höhere Isolationsstufe jedoch keine niedrigere Stufe erfolgreich anfordern.  
  
## <a name="immediate-and-delayed-update-modes"></a>Unmittelbarer und verzögerter Updatemodus  
 Im Sofortupdatemodus verursacht jeder Aufruf von **IRowsetChange::SetData** einen Roundtrip zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn der Consumer mehrere Änderungen an einer einzelnen Zeile vornimmt, ist es effizienter, alle Änderungen mit einem einzigen **SetData**-Aufruf zu übergeben.  
  
 Im verzögerten Updatemodus wird für jede im *cRows*-Parameter und *rghRows*-Parameter von **IRowsetUpdate::Update** angegebene Zeile ein Roundtrip zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchgeführt.  
  
 In beiden Modi stellt ein Roundtrip eine separate Transaktion dar, wenn kein Transaktionsobjekt für das Rowset geöffnet ist.  
  
 Bei Verwendung **IRowsetUpdate:: Update**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, jede angegebene Zeile zu verarbeiten. Einen Fehler aufgrund ungültiger Daten-, Länge oder Status-Werte für jede Zeile nicht angehalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verarbeitet. Es können nur alle oder keine der anderen am Update beteiligten Zeilen geändert werden. Der Consumer muss das zurückgegebene untersuchen *PrgRowStatus* Array zum Ermitteln von Fehlern für jede spezifische Datenzeile, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück.  
  
 Ein Consumer darf nicht davon ausgehen, dass Zeilen in einer bestimmten Reihenfolge verarbeitet werden. Wenn ein Consumer es erfordert, dass die Verarbeitung von Datenänderungen in mehr als einer Zeile in einer bestimmten Reihenfolge durchgeführt wird, muss der Consumer diese Reihenfolge in der Anwendungslogik festlegen und eine Transaktion öffnen, um den Prozess darin einzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Daten in Rowsets](updating-data-in-rowsets.md)  
  
  
