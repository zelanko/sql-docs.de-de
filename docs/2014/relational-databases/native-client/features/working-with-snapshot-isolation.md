---
title: Arbeiten mit der Momentaufnahme Isolation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcf2003873de6f6ca15fed4d0818337ce4920906
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63205857"
---
# <a name="working-with-snapshot-isolation"></a>Arbeiten mit Momentaufnahmeisolation
  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde eine neue Momentaufnahmenisolationsstufe eingeführt, die die Parallelität für OLTP-Anwendungen (Online Transaction Processing, Onlinetransaktionsverarbeitung) verbessern soll. In früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basierte die Parallelität ausschließlich auf dem Sperren, was zu Blockierungs- und Deadlockproblemen bei einigen Anwendungen führen konnte. Die Momentaufnahmenisolation hängt von Verbesserungen der Zeilenversionsverwaltung ab und soll die Leistung durch Vermeidung von Leser-/Schreiberblockierungsszenarien erhöhen.  
  
 Transaktionen, die mit der Momentaufnahmenisolation gestartet werden, lesen eine Datenbankmomentaufnahme zu dem Zeitpunkt, an dem die Transaktion gestartet wird. Eine Folge davon ist, dass sich keysetgesteuerte, dynamische und statische Servercursor, wenn sie innerhalb eines Momentaufnahmentransaktionskontexts geöffnet werden, ähnlich verhalten wie statische Cursor, die innerhalb serialisierbarer Transaktionen geöffnet werden. Wenn die Cursor unter der Momentaufnahmenisolationsstufe geöffnet werden, werden jedoch keine Sperren angenommen, was sich positiv auf die Blockierung des Servers auswirken kann.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verfügt über Erweiterungen, die die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]eingeführte Snapshot-Isolation nutzen. Diese Erweiterungen schließen Änderungen an den DBPROPSET_DATASOURCEINFO und DBPROPSET_SESSION-Eigenschaftsgruppen ein.  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Die DBPROPSET_DATASOURCEINFO-Eigenschaftsgruppe wurde geändert, um anzugeben, dass die Momentaufnahmenisolationsstufe vom hinzugefügten DBPROPVAL_TI_SNAPSHOT-Wert unterstützt wird, der in der DBPROP_SUPPORTEDTXNISOLEVELS-Eigenschaft verwendet wird. Dieser neue Wert gibt an, dass die Momentaufnahmenisolationsstufe unabhängig davon unterstützt wird, ob die Versionsverwaltung für die Datenbank aktiviert ist. Im Folgenden sind die DBPROP_SUPPORTEDTXNISOLEVELS-Werte aufgeführt:  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Typ: VT_I4<br /><br /> R/W: Schreibgeschützt<br /><br /> Beschreibung: Eine Bitmaske, die die unterstützten Transaktionsisolationsstufen angibt. Eine Kombination von null oder mehreren der folgenden Werte:<br /><br /> -DBPROPVAL_TI_CHAOS<br />-DBPROPVAL_TI_READUNCOMMITTED<br />-DBPROPVAL_TI_BROWSE<br />-DBPROPVAL_TI_CURSORSTABILITY<br />-DBPROPVAL_TI_READCOMMITTED<br />-DBPROPVAL_TI_REPEATABLEREAD<br />-DBPROPVAL_TI_SERIALIZABLE<br />-DBPROPVAL_TI_ISOLATED<br />-DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>DBPROPSET_SESSION  
 Die DBPROPSET_SESSION-Eigenschaftsgruppe wurde geändert, um anzugeben, dass die Momentaufnahmenisolationsstufe vom hinzugefügten DBPROPVAL_TI_SNAPSHOT-Wert unterstützt wird, der in der DBPROP_SESS_AUTOCOMMITISOLEVELS-Eigenschaft verwendet wird. Dieser neue Wert gibt an, dass die Momentaufnahmenisolationsstufe unabhängig davon unterstützt wird, ob die Versionsverwaltung für die Datenbank aktiviert ist. Im Folgenden sind die DBPROP_SESS_AUTOCOMMITISOLEVELS-Werte aufgeführt:  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Typ: VT_I4<br /><br /> R/W: Schreibgeschützt<br /><br /> Beschreibung: Legt eine Bitmaske fest, die die Transaktionsisolationsstufe im Autocommit-Modus angibt. Die Werte, die in dieser Bitmaske festgelegt werden können, entsprechen den für DBPROP_SUPPORTEDTXNISOLEVELS möglichen Werten.|  
  
> [!NOTE]  
>  Der Fehler DB_S_ERRORSOCCURRED oder DB_E_ERRORSOCCURRED tritt auf, wenn DBPROPVAL_TI_SNAPSHOT in Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt wird.  
  
 Informationen dazu, wie Snapshot-Isolation in Transaktionen unterstützt wird, finden Sie [unter unterstützen lokaler Transaktionen](../../native-client-ole-db-transactions/transactions.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber bietet Unterstützung für die Momentaufnahme Isolation, wobei jedoch Erweiterungen an den Funktionen [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) vorgenommen werden.  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Die **SQLSetConnectAttr** -Funktion unterstützt jetzt die Verwendung des SQL_COPT_SS_TXN_ISOLATION-Attributs. Durch Festlegen von SQL_COPT_SS_TXN_ISOLATION auf SQL_TXN_SS_SNAPSHOT wird angegeben, dass die Transaktion unter der Momentaufnahmeisolationsstufe ausgeführt wird.  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 Die [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) -Funktion unterstützt jetzt den SQL_TXN_SS_SNAPSHOT Wert, der dem SQL_TXN_ISOLATION_OPTION Infotyp hinzugefügt wurde.  
  
 Informationen zur Unterstützung von Snapshot-Isolation in Transaktionen finden Sie unter [Cursor Transaktions Isolationsstufe](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)   
 [Eigenschaften und Verhaltensweisen von Rowsets](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
