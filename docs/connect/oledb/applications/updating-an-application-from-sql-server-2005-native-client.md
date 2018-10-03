---
title: Aktualisieren einer Anwendung von SQL Server 2005 Native Client | Microsoft-Dokumentation
description: Aktualisieren einer Anwendung von SQL Server 2005 Native Client
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d8a32569f9d7125505c6d50235a2dc17e19a7408
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804328"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aktualisieren einer Anwendung von SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Thema werden die wichtigen Änderungen in OLE DB-Treiber für SQL Server seit erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

 Wenn Sie ein Upgrade von Microsoft Data Access Components (MDAC) auf OLE DB-Treiber für SQL Server durchführen, werden Ihnen möglicherweise auch einige Unterschiede im Verhalten auffallen. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung auf OLE DB-Treiber für SQL Server über MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 war im Lieferumfang von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 war im Lieferumfang von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] enthalten.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 war im Lieferumfang von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 war im Lieferumfang von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] enthalten.  

|Geändert von Verhalten in OLE DB-Treiber für SQL Server im Vergleich zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|und Beschreibung|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB füllt nur Zahlen bis zur definierten Anzahl von Dezimalstellen auf.|Für Konvertierungen aus, in dem konvertierte Daten an den Server gesendet werden, füllt der OLE DB-Treiber für SQL Server nachfolgende Nullen in Daten nur bis zur maximalen Länge von **"DateTime"** Werte. In SQL Server Native Client 9.0 wurden Zahlen bis zu 9 Stellen aufgefüllt.|  
|Überprüfen Sie DBTYPE_DBTIMESTAMP für ICommandWithParameter::SetParameterInfo.|OLE DB-Treiber für SQL Server implementiert die OLE DB-Anforderung für *bScale* in ICommandWithParameter::SetParameterInfo, um die Genauigkeit der Sekundenbruchteile für DBTYPE_DBTIMESTAMP festgelegt werden.|  
|Die **Sp_columns** gibt die gespeicherte Prozedur **"NO"** anstelle von **"NO"** für die Spalte IS_NULLABLE.|In OLE DB-Treiber für SQL Server **Sp_columns** gibt die gespeicherte Prozedur **"NO"** anstelle von **"NO"** für eine IS_NULLABLE-Spalte.|  
|Es wird ein anderer Fehler zurückgegeben, wenn das Datum außerhalb des zulässigen Bereichs liegt.|Für die **"DateTime"** Typ, eine andere Fehlernummer von zurückgegeben werden, OLE DB-Treiber für SQL Server für ein Datum außerhalb des gültigen Bereichs als in früheren Versionen zurückgegeben wurde.<br /><br /> Insbesondere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 gab 22007 für alle Jahreswerte in zeichenfolgenkonvertierungen **"DateTime"**, und der OLE DB-Treiber für SQL Server die Fehlernummer 22008 zurück, wenn das Datum innerhalb des Bereichs von unterstützt**datetime2** jedoch außerhalb des Bereichs von unterstützten **"DateTime"** oder **Smalldatetime**.|  
|Bei **datetime**-Werten werden Sekundenbruchteile abgeschnitten, und diese Werte werden nicht gerundet, wenn sich durch die Rundung der Tag ändern würde.|In Versionen vor [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 wurden **datetime**-Werte, die an den Server gesendet wurden, vom Client auf das nächste 1/300stel einer Sekunde gerundet. In OLE DB-Treiber für SQL Server bewirkt, dass dieses Szenario ein Abschneiden von Sekundenbruchteilen Wenn Rundung den Tag ändert.|  
|Mögliche ein Abschneiden der Sekunden für **"DateTime"** Wert.|Eine Anwendung, die mit OLE DB-Treiber für SQL Server erstellt wurde, die eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-2005-Server herstellt, schneidet Sekunden und Sekundenbruchteile für den Zeitteil der Daten ab, die an den Server gesendet werden, wenn Sie an eine datetime-Spalte mit dem Typbezeichner DBTYPE_DBTIMESTAMP (OLE DB) oder SQL_TIMESTAMP (ODBC) und der Skala 0 binden.<br /><br /> Zum Beispiel:<br /><br /> Eingabedaten: 1994-08-21 21:21:36.000<br /><br /> Einfügedaten: 1994-08-21 21:21:00.000|  
|Die OLE DB-Datenkonvertierung von DBTYPE_DBTIME in DBTYPE_DATE kann keine Änderung des Tages mehr bewirken.|In früheren Versionen als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 bewirkte der OLE DB-Konvertierungscode eine Änderung des Tages, wenn der Uhrzeitanteil eines DBTYPE_DATE-Werts innerhalb einer halben Sekunde vor Mitternacht lag. In OLE DB-Treiber für SQL Server, das Tag wird nicht geändert (Sekundenbruchteile werden abgeschnitten und nicht gerundet).|  
|IBCPSession::BCColFmt Konvertierung ändert.|Bei Verwendung von IBCPSession::BCOColFmt SQLDATETIME oder SQLDATETIME in einen Zeichenfolgen-Datentyp zu konvertieren, wird im OLE DB-Treiber für SQL Server ein Dezimalstellenwert exportiert. Wenn beispielsweise der Typ SQLDATETIME in den Typ SQLNVARCHARMAX konvertiert wurde, gaben Vorgängerversionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 Folgendes zurück:<br /> 1989-02-01 00:00:00.<br />OLE DB-Treiber für SQL Server gibt Folgendes zurück: <br />1989-02-01 00:00:00.0000000.|  
|Benutzerdefinierte Anwendungen, die die BCP API verwenden, können jetzt Warnungen anzeigen.|Die BCP API erzeugt jetzt für alle Typen Warnmeldungen, wenn die Datenlänge die angegebene Länge eines Felds überschreitet. Früher wurde diese Warnung nur für Zeichentypen ausgegeben, aber nicht für alle Typen.|  
|Wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wird, die an einen Datum-/Uhrzeit-Typ gebunden wurde, dann wird dadurch ein Fehler erzeugt.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 wurde kein Fehler erzeugt, wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wurde, die an einen Datum-/Uhrzeit-Typ gebunden war. OLE DB-Treiber für SQL Server generiert in dieser Situation ordnungsgemäß einen Fehler auf.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann andere Ergebnisse zurückgeben, wenn ein Trigger ausgeführt wird.|In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Änderungen können bewirken, dass für eine Anwendung andere Ergebnisse von einer Anweisung zurückgegeben werden, die die Ausführung eines Triggers verursachen, wenn **NOCOUNT OFF** gültig war. In dieser Situation kann die Anwendung einen Fehler generieren. Um diesen Fehler zu beheben, legen **NOCOUNT ON** im Trigger.|  

## <a name="see-also"></a>Weitere Informationen finden Sie unter   
 [OLE DB-Treiber für SQL-Server](../../oledb/oledb-driver-for-sql-server.md)
