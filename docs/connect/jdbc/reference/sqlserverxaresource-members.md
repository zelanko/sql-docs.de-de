---
title: SQLServerXAResource-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c8b3e731fdc3480d646e141cbd53b777407015f8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768273"
---
# <a name="sqlserverxaresource-members"></a>SQLServerXAResource-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  In den folgenden Tabellen sind die Elemente aufgeführt, die von der [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|Hierdurch werden eng verkoppelte XA-Transaktionen ermöglicht, die unterschiedliche XA-Verzweigungstransaktions-IDs (XIDs) aber dieselbe globale Transaktions-ID (GTRID) aufweisen.|  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|Führt einen Commit für die globale Transaktion aus, die durch das angegebene Xid-Objekt festgelegt wird.|  
|[end](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|Beendet die für einen Transaktionszweig durchgeführte Arbeit.|  
|[forget](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|Teilt dem Ressourcen-Manager mit, dass eine heuristisch abgeschlossene Transaktionsverzweigung ignoriert (vergessen) werden kann.|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|Ruft den aktuellen Transaktionstimeoutwert für das [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekt ab.|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|Ermittelt, ob die vom Zielobjekt dargestellte Ressourcen-Manager-Instanz der vom XAResource-Objekt dargestellten Ressourcen-Manager-Instanz entspricht.|  
|[prepare](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|Fordert an, dass der Ressourcen-Manager für eine Transaktions-Commit-Aktion der vom vorhandenen Xid-Objekt angegebenen Transaktion vorbereitet wird.|  
|[Wiederherstellen](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|Ruft eine Liste vorbereiteter Transaktionszweige von einem Ressourcen-Manager ab.|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|Fordert an, dass der Ressourcen-Manager für die für den Transaktionszweig durchgeführte Arbeit ein Rollback ausführt.|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|Legt den aktuellen Transaktionstimeoutwert für das [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) -Objekt fest.|  
|[start](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Startet die Arbeit am Xid-Objekt, das in einem Transaktionszweig angegeben ist.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
