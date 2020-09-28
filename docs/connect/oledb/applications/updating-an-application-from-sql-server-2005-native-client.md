---
title: Aktualisieren einer Anwendung von SQL Server 2005 Native Client | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Breaking Changes im OLE DB-Treiber für SQL Server seit SQL Server Native Client in SQL Server 2005 (9.x).
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40b101c189832a91dd06d1bba58b17c341d11130
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860041"
---
# <a name="updating-applications-from-sql-server-2005-native-client"></a>Aktualisieren von Anwendungen von SQL Server 2005 Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Thema werden die aktuellen Änderungen im OLE DB-Treiber für SQL Server seit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] erläutert.  

 Wenn Sie ein Upgrade von Microsoft Data Access Components (MDAC) auf OLE DB-Treiber für SQL Server durchführen, werden Ihnen möglicherweise auch einige Unterschiede im Verhalten auffallen. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 war im Lieferumfang von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 war im Lieferumfang von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] enthalten.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 war im Lieferumfang von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 war im Lieferumfang von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] enthalten.  

|Geändertes Verhalten im OLE DB-Treiber für SQL Server im Vergleich zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|BESCHREIBUNG|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB füllt nur Zahlen bis zur definierten Anzahl von Dezimalstellen auf.|In Konvertierungen, bei denen Daten an den Server gesendet werden, füllt der OLE DB-Treiber für SQL Server nachfolgende Nullen in Daten nur bis zur maximalen Länge von **datetime**-Werten auf. In SQL Server Native Client 9.0 wurden Zahlen bis zu 9 Stellen aufgefüllt.|  
|Überprüfen Sie DBTYPE_DBTIMESTAMP auf ICommandWithParameter::SetParameterInfo.|Der OLE DB-Treiber für SQL Server implementiert die OLE DB-Anforderung, dass *bScale* in ICommandWithParameter::SetParameterInfo für DBTYPE_DBTIMESTAMP auf Sekundenbruchteile genau festgelegt wird.|  
|Die gespeicherte Prozedur **sp_columns** gibt jetzt für die Spalte IS_NULLABLE **„NO“** statt **„NO“** zurück.|Im OLE DB-Treiber für SQL Server gibt die gespeicherte Prozedur **sp_columns** jetzt für eine IS_NULLABLE-Spalte **„NO“** statt **„NO“** zurück.|  
|Es wird ein anderer Fehler zurückgegeben, wenn das Datum außerhalb des zulässigen Bereichs liegt.|Für den **datetime**-Typ gibt der OLE DB-Treiber für SQL Server eine andere Fehlernummer für ein außerhalb des gültigen Bereichs liegendes Datum zurück als frühere Versionen.<br /><br /> Das heißt, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 gab in Zeichenfolgenkonvertierungen in **datetime** die Fehlernummer 22007 für alle Jahreswerte zurück, die außerhalb des zulässigen Bereichs lagen, und der OLE DB-Treiber für SQL Server gibt die Fehlernummer 22008 zurück, wenn das Datum innerhalb des von **datetime2** unterstützten Bereichs, aber außerhalb des von **datetime** oder **smalldatetime** unterstützten Bereichs liegt.|  
|Bei **datetime**-Werten werden Sekundenbruchteile abgeschnitten, und diese Werte werden nicht gerundet, wenn sich durch die Rundung der Tag ändern würde.|In Versionen vor [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 wurden **datetime**-Werte, die an den Server gesendet wurden, vom Client auf das nächste 1/300stel einer Sekunde gerundet. Im OLE DB-Treiber für SQL Server werden in diesem Szenario die Sekundenbruchteile abgeschnitten, wenn die Rundung eine Änderung des Tags bewirkt.|  
|Möglicherweise werden vom **datetime**-Wert Sekunden abgeschnitten.|Eine Anwendung, die mit OLE DB-Treiber für SQL Server erstellt wurde, die eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-2005-Server herstellt, schneidet Sekunden und Sekundenbruchteile für den Zeitteil der Daten ab, die an den Server gesendet werden, wenn Sie an eine datetime-Spalte mit dem Typbezeichner DBTYPE_DBTIMESTAMP (OLE DB) oder SQL_TIMESTAMP (ODBC) und der Skala 0 binden.<br /><br /> Beispiel:<br /><br /> Eingabedaten: 1994-08-21 21:21:36.000<br /><br /> Einfügedaten: 1994-08-21 21:21:00.000|  
|Die OLE DB-Datenkonvertierung von DBTYPE_DBTIME in DBTYPE_DATE kann keine Änderung des Tages mehr bewirken.|In früheren Versionen als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 bewirkte der OLE DB-Konvertierungscode eine Änderung des Tages, wenn der Uhrzeitanteil eines DBTYPE_DATE-Werts innerhalb einer halben Sekunde vor Mitternacht lag. Im OLE DB-Treiber für SQL Server wird der Tag nicht geändert (Sekundenbruchteile werden abgeschnitten und nicht gerundet).|  
|IBCPSession::BCColFmt-Konvertierungsänderungen.|Wenn Sie im OLE DB-Treiber für SQL Server IBCPSession::BCOColFmt verwenden, um SQLDATETIME zu konvertieren oder SQLDATETIME in einen Zeichenfolgentyp zu konvertieren, wird ein Bruchwert exportiert. Wenn beispielsweise der Typ SQLDATETIME in den Typ SQLNVARCHARMAX konvertiert wurde, gaben Vorgängerversionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 Folgendes zurück:<br /> 1989-02-01 00:00:00.<br />OLE DB-Treiber für SQL Server gibt Folgendes zurück: <br />1989-02-01 00:00:00.0000000.|  
|Benutzerdefinierte Anwendungen, die die BCP API verwenden, können jetzt Warnungen anzeigen.|Die BCP API erzeugt jetzt für alle Typen Warnmeldungen, wenn die Datenlänge die angegebene Länge eines Felds überschreitet. Früher wurde diese Warnung nur für Zeichentypen ausgegeben, aber nicht für alle Typen.|  
|Wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wird, die an einen Datum-/Uhrzeit-Typ gebunden wurde, dann wird dadurch ein Fehler erzeugt.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 wurde kein Fehler erzeugt, wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wurde, die an einen Datum-/Uhrzeit-Typ gebunden war. Der OLE DB-Treiber für SQL Server generiert in dieser Situation ordnungsgemäß einen Fehler.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann andere Ergebnisse zurückgeben, wenn ein Trigger ausgeführt wird.|In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Änderungen können bewirken, dass für eine Anwendung andere Ergebnisse von einer Anweisung zurückgegeben werden, die die Ausführung eines Triggers verursachen, wenn **NOCOUNT OFF** gültig war. In dieser Situation kann die Anwendung einen Fehler generieren. Legen Sie **NOCOUNT ON** im Trigger fest, um diesen Fehler zu beheben.|  

## <a name="see-also"></a>Weitere Informationen   
 [OLE DB-Treiber für SQL-Server](../../oledb/oledb-driver-for-sql-server.md)
