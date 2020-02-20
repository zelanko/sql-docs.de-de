---
title: Verwenden der Momentaufnahmenisolation | Microsoft-Dokumentation
description: Verwenden der Momentaufnahmenisolation im OLE DB Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], snapshot isolation
- MSOLEDBSQL, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, snapshot isolation
- SQLGetInfo function
- concurrency [OLE DB Driver for SQL Server]
- SQLSetConnectAttr function
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 25d3dbaf09e5cdd6dc6726402275376766cf0591
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67988688"
---
# <a name="working-with-snapshot-isolation"></a>Arbeiten mit Momentaufnahmeisolation
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde eine neue Momentaufnahmenisolationsstufe eingeführt, die die Parallelität für OLTP-Anwendungen (Online Transaction Processing, Onlinetransaktionsverarbeitung) verbessern soll. In früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basierte die Parallelität ausschließlich auf dem Sperren, was zu Blockierungs- und Deadlockproblemen bei einigen Anwendungen führen konnte. Die Momentaufnahmenisolation hängt von Verbesserungen der Zeilenversionsverwaltung ab und soll die Leistung durch Vermeidung von Leser-/Schreiberblockierungsszenarien erhöhen.  
  
 Transaktionen, die mit der Momentaufnahmenisolation gestartet werden, lesen eine Datenbankmomentaufnahme zu dem Zeitpunkt, an dem die Transaktion gestartet wird. Keysetgesteuerte, dynamische und statische Servercursors verhalten sich, wenn sie innerhalb des Kontexts einer Momentaufnahmentransaktion geöffnet werden, ähnlich wie statische Cursors, die innerhalb von serialisierbaren Transaktionen geöffnet werden. Wenn die Cursor unter der Momentaufnahmenisolationsstufe geöffnet werden, werden jedoch keine Sperren angenommen. Das kann sich positiv auf die Blockierung des Servers auswirken.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server verfügt über Verbesserungen, die die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführte Momentaufnahmenisolation nutzen. Diese Erweiterungen schließen Änderungen an den DBPROPSET_DATASOURCEINFO und DBPROPSET_SESSION-Eigenschaftsgruppen ein.  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Die DBPROPSET_DATASOURCEINFO-Eigenschaftsgruppe wurde geändert, um anzugeben, dass die Momentaufnahmenisolationsstufe vom hinzugefügten DBPROPVAL_TI_SNAPSHOT-Wert unterstützt wird, der in der DBPROP_SUPPORTEDTXNISOLEVELS-Eigenschaft verwendet wird. Dieser neue Wert gibt an, dass die Momentaufnahmenisolationsstufe unabhängig davon unterstützt wird, ob die Versionsverwaltung für die Datenbank aktiviert ist. Die folgende Tabelle enthält die Werte für DBPROP_SUPPORTEDTXNISOLEVELS:  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Typ: VT_I4<br /><br /> R/W: Nur Lesezugriff<br /><br /> Beschreibung: Eine Bitmaske, die die unterstützten Transaktionsisolationsstufen angibt. Eine Kombination von null oder mehreren der folgenden Werte:<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>DBPROPSET_SESSION  
 Die DBPROPSET_SESSION-Eigenschaftsgruppe wurde geändert, um anzugeben, dass die Momentaufnahmenisolationsstufe vom hinzugefügten DBPROPVAL_TI_SNAPSHOT-Wert unterstützt wird, der in der DBPROP_SESS_AUTOCOMMITISOLEVELS-Eigenschaft verwendet wird. Dieser neue Wert gibt an, dass die Momentaufnahmenisolationsstufe unabhängig davon unterstützt wird, ob die Versionsverwaltung für die Datenbank aktiviert ist. In der folgenden Tabelle sind die DBPROP_SESS_AUTOCOMMITISOLEVELS-Werte aufgeführt:
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Typ: VT_I4<br /><br /> R/W: Nur Lesezugriff<br /><br /> Beschreibung: Legt eine Bitmaske fest, die die Transaktionsisolationsstufe im Modus „automatischer Commit“ angibt. Die Werte, die in dieser Bitmaske festgelegt werden können, entsprechen den für DBPROP_SUPPORTEDTXNISOLEVELS möglichen Werten.|  
  
> [!NOTE]  
>  Der Fehler DB_S_ERRORSOCCURRED oder DB_E_ERRORSOCCURRED tritt auf, wenn DBPROPVAL_TI_SNAPSHOT in Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt wird.  
  
 Weitere Informationen dazu, wie die Momentaufnahmenisolation in Transaktionen unterstützt wird, finden Sie unter [Unterstützen lokaler Transaktionen](../../oledb/ole-db-transactions/supporting-local-transactions.md).  

  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Eigenschaften und Verhaltensweisen von Rowsets](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
