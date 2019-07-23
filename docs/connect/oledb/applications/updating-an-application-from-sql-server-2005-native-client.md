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
ms.openlocfilehash: 7915b9fb74f05057e05eef022d7f9b0e4ccdd21f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989248"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aktualisieren einer Anwendung von SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Thema werden die wichtigen Änderungen in OLE DB Treiber für SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] seit Native Client [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]in erläutert.  

 Wenn Sie ein Upgrade von Microsoft Data Access Components (MDAC) auf OLE DB-Treiber für SQL Server durchführen, werden Ihnen möglicherweise auch einige Unterschiede im Verhalten auffallen. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung auf OLE DB Treiber für SQL Server von MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 war im Lieferumfang von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 war im Lieferumfang von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] enthalten.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 war im Lieferumfang von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] enthalten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 war im Lieferumfang von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] enthalten.  

|Geändertes Verhalten in OLE DB Treiber für SQL Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] im Vergleich zu Native Client|und Beschreibung|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB füllt nur Zahlen bis zur definierten Anzahl von Dezimalstellen auf.|Bei Konvertierungen, bei denen konvertierte Daten an den Server gesendet werden, OLE DB Treiber für SQL Server nachfolgende Nullen in Daten nur bis zur maximalen Länge von **DateTime** -Werten. In SQL Server Native Client 9.0 wurden Zahlen bis zu 9 Stellen aufgefüllt.|  
|Validate DBTYPE_DBTIMESTAMP für ICommandWithParameter:: SetParameterInfo.|OLE DB Treiber für SQL Server implementiert die OLE DB Anforderung für *bScale* in ICommandWithParameter:: SetParameterInfo, damit Sie auf die Genauigkeit der Sekundenbruchteile für DBTYPE_DBTIMESTAMP festgelegt wird.|  
|Die gespeicherte Prozedur **sp_columns** gibt jetzt **"No"** anstelle von **"No"** für die IS_NULLABLE-Spalte zurück.|In OLE DB Treiber für SQL Server gibt die gespeicherte Prozedur **sp_columns** jetzt **"No"** anstelle von **"No"** für eine IS_NULLABLE-Spalte zurück.|  
|Es wird ein anderer Fehler zurückgegeben, wenn das Datum außerhalb des zulässigen Bereichs liegt.|Für den **DateTime** -Typ wird von OLE DB Treiber eine andere Fehlernummer zurückgegeben, für die SQL Server einen Zeitraum außerhalb des gültigen Bereichs als in früheren Versionen zurückgegeben hat.<br /><br /> Der Native Client 9,0 hat 22007 für alle Werte des Jahres Werts in Zeichen folgen Konvertierungen in **DateTime**zurückgegeben, und OLE DB Treiber für SQL Server gibt 22008 zurück, wenn das Datum innerhalb des von **datetime2** unterstützten Bereichs liegt, aber außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der von " **DateTime** " oder " **smalldatetime**" unterstützte Bereich.|  
|Bei **datetime**-Werten werden Sekundenbruchteile abgeschnitten, und diese Werte werden nicht gerundet, wenn sich durch die Rundung der Tag ändern würde.|In Versionen vor [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 wurden **datetime**-Werte, die an den Server gesendet wurden, vom Client auf das nächste 1/300stel einer Sekunde gerundet. In OLE DB Treiber für SQL Server bewirkt dieses Szenario ein Abschneiden von Sekundenbruchteilen, wenn die Rundung den Tag ändert.|  
|Mögliche Verkürzung von Sekunden für den **DateTime** -Wert.|Eine Anwendung, die mit OLE DB-Treiber für SQL Server erstellt wurde, die eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-2005-Server herstellt, schneidet Sekunden und Sekundenbruchteile für den Zeitteil der Daten ab, die an den Server gesendet werden, wenn Sie an eine datetime-Spalte mit dem Typbezeichner DBTYPE_DBTIMESTAMP (OLE DB) oder SQL_TIMESTAMP (ODBC) und der Skala 0 binden.<br /><br /> Beispiel:<br /><br /> Eingabedaten: 1994-08-21 21:21:36.000<br /><br /> Einfügedaten: 1994-08-21 21:21:00.000|  
|Die OLE DB-Datenkonvertierung von DBTYPE_DBTIME in DBTYPE_DATE kann keine Änderung des Tages mehr bewirken.|In früheren Versionen als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 bewirkte der OLE DB-Konvertierungscode eine Änderung des Tages, wenn der Uhrzeitanteil eines DBTYPE_DATE-Werts innerhalb einer halben Sekunde vor Mitternacht lag. In OLE DB Treiber für SQL Server ändert sich der Tag nicht (Sekundenbruchteile werden abgeschnitten und nicht gerundet).|  
|Die IBCPSession:: bccolbmt-Konvertierung ändert sich.|Wenn Sie in OLE DB Driver for SQL Server "IBCPSession:: BCOColFmt" verwenden, um SqlDateTime oder SqlDateTime in einen Zeichen Folgentyp zu konvertieren, wird ein Bruch Wert exportiert. Wenn beispielsweise der Typ SQLDATETIME in den Typ SQLNVARCHARMAX konvertiert wurde, gaben Vorgängerversionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 Folgendes zurück:<br /> 1989-02-01 00:00:00.<br />OLE DB-Treiber für SQL Server gibt Folgendes zurück: <br />1989-02-01 00:00:00.0000000.|  
|Benutzerdefinierte Anwendungen, die die BCP API verwenden, können jetzt Warnungen anzeigen.|Die BCP API erzeugt jetzt für alle Typen Warnmeldungen, wenn die Datenlänge die angegebene Länge eines Felds überschreitet. Früher wurde diese Warnung nur für Zeichentypen ausgegeben, aber nicht für alle Typen.|  
|Wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wird, die an einen Datum-/Uhrzeit-Typ gebunden wurde, dann wird dadurch ein Fehler erzeugt.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 wurde kein Fehler erzeugt, wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wurde, die an einen Datum-/Uhrzeit-Typ gebunden war. OLE DB Treiber für SQL Server generiert in dieser Situation ordnungsgemäß einen Fehler.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann andere Ergebnisse zurückgeben, wenn ein Trigger ausgeführt wird.|In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Änderungen können bewirken, dass für eine Anwendung andere Ergebnisse von einer Anweisung zurückgegeben werden, die die Ausführung eines Triggers verursachen, wenn **NOCOUNT OFF** gültig war. In dieser Situation kann die Anwendung einen Fehler generieren. Legen Sie zum Beheben dieses Fehlers **NOCOUNT** im-Wert fest.|  

## <a name="see-also"></a>Weitere Informationen   
 [OLE DB-Treiber für SQL-Server](../../oledb/oledb-driver-for-sql-server.md)
