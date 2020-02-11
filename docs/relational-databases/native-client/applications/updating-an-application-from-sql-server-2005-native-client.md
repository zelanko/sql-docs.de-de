---
title: Native Client, Update App SQL 2005
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2eddd2284ec77a1a4979389f964baeafb6932dc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243812"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aktualisieren einer Anwendung von SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema werden die aktuellen Änderungen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client seit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] erläutert.  
  
 Wenn Sie ein Upgrade von Microsoft Data Access Components (MDAC) auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client durchführen, werden Ihnen möglicherweise auch einige Unterschiede im Verhalten auffallen. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung in SQL Server Native Client von MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 war im Lieferumfang von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] enthalten. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 war im Lieferumfang von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] enthalten.  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 war im Lieferumfang von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] enthalten. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 war im Lieferumfang von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] enthalten.  
  
|Geändertes Verhalten in SQL Server Native Client seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|BESCHREIBUNG|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB füllt nur Zahlen bis zur definierten Anzahl von Dezimalstellen auf.|Bei Konvertierungen, bei denen konvertierte Daten an den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Server gesendet werden, füllt [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]Native Client (beginnend mit) nachfolgende Nullen in Daten nur bis zur maximalen Länge von **DateTime** -Werten auf. In SQL Server Native Client 9.0 wurden Zahlen bis zu 9 Stellen aufgefüllt.|  
|Überprüfen Sie DBTYPE_DBTIMESTAMP für ICommandWithParameter:: SetParameterInfo.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client (ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) implementiert die OLE DB Anforderung für *bScale* in ICommandWithParameter:: SetParameterInfo, um für DBTYPE_DBTIMESTAMP auf die Genauigkeit der Sekundenbruchteile festzulegen.|  
|Die gespeicherte Prozedur **sp_columns** gibt jetzt **"No"** anstelle von **"No"** für die IS_NULLABLE Spalte zurück.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Ab Native Client 10,0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) gibt **sp_columns** gespeicherte Prozedur jetzt **"No"** anstelle von **"No"** für eine IS_NULLABLE Spalte zurück.|  
|Sqlsetdebug, SQLBindParameter und SQLBindCol führen nun eine Konsistenzprüfung durch.|Vor dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0 hat das Festlegen von SQL_DESC_DATA_PTR keine Konsistenzprüfung für einen Deskriptortyp in SQLSetDescRec, SQLBindParameter oder SQLBindCol verursacht.|  
|Sqlcopydebug führt jetzt eine Deskriptorkonsistenz Prüfung durch.|Vor dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0 hat SQLCopyDesc keine Konsistenzprüfung durchgeführt, wenn das SQL_DESC_DATA_PTR Feld für einen bestimmten Datensatz festgelegt wurde.|  
|Sqlgetdebug führt keine deskriptorkonsistenzprüfung mehr durch.|Vor dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0 hat SQLGetDescRec eine Deskriptorkonsistenz Prüfung durchgeführt, als das SQL_DESC_DATA_PTR Feld festgelegt wurde. Die ODBC-Spezifikation erfordert dies nicht, und in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) sowie in höheren Versionen wird diese Konsistenzprüfung nicht mehr ausgeführt.|  
|Es wird ein anderer Fehler zurückgegeben, wenn das Datum außerhalb des zulässigen Bereichs liegt.|Für den **DateTime** -Typ wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) eine andere Fehlernummer für ein außerhalb des gültigen Bereichs gegebenes Datum zurückgegeben, als in früheren Versionen zurückgegeben wurde.<br /><br /> Insbesondere gibt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9,0 22007 für alle Werte des Jahres Werts in Zeichen folgen Konvertierungen in **DateTime**zurück, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und Native Client ab Version 10,0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) gibt 22008 zurück, wenn das Datum innerhalb des von **datetime2** unterstützten Bereichs liegt, jedoch außerhalb des von **DateTime** oder **smalldatetime**unterstützten Bereichs.|  
|der **DateTime** -Wert verkürzt Sekundenbruchteile und ist nicht abgerundet, wenn die Rundung den Tag ändert.|In Versionen vor [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 wurden **datetime**-Werte, die an den Server gesendet wurden, vom Client auf das nächste 1/300stel einer Sekunde gerundet. Ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 werden in diesem Szenario die Sekundenbruchteile abgeschnitten, wenn die Rundung eine Änderung des Tags bewirkt.|  
|Mögliche Verkürzung von Sekunden für den **DateTime** -Wert.|Eine Anwendung, die mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (oder höher) erstellt wurde, die eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005-Server herstellt, schneidet Sekunden und Sekundenbruchteile für den Zeitteil der Daten ab, die an den Server gesendet werden, wenn Sie an eine datetime-Spalte mit dem Typbezeichner DBTYPE_DBTIMESTAMP (OLE DB) oder SQL_TIMESTAMP (ODBC) und der Skala 0 binden.<br /><br /> Beispiel:<br /><br /> Eingabedaten: 1994-08-21 21:21:36.000<br /><br /> Einfügedaten: 1994-08-21 21:21:00.000|  
|Die OLE DB-Datenkonvertierung von DBTYPE_DBTIME in DBTYPE_DATE kann keine Änderung des Tages mehr bewirken.|In früheren Versionen als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 bewirkte der OLE DB-Konvertierungscode eine Änderung des Tages, wenn der Uhrzeitanteil eines DBTYPE_DATE-Werts innerhalb einer halben Sekunde vor Mitternacht lag. Ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 wird der Tag nicht geändert (Sekundenbruchteile werden abgeschnitten und nicht gerundet).|  
|Die IBCPSession:: bccolbmt-Konvertierung ändert sich.|Wenn Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in Native Client 10,0 verwenden, wenn Sie IBCPSession:: BCOColFmt verwenden, um SqlDateTime oder SqlDateTime in einen Zeichen Folgentyp zu konvertieren, wird ein Bruchteil-Wert exportiert. Wenn beispielsweise der Typ SQLDATETIME in den Typ SQLNVARCHARMAX konvertiert wird, gaben Vorgängerversionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Folgendes zurück:<br /><br /> 1989-02-01 00:00:00. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 und höhere Versionen geben 1989-02-01 00:00:00.0000000 zurück.|  
|Die Größe der gesendeten Daten muss der in SQL_LEN_DATA_AT_EXEC angegebenen Länge entsprechen.|Wenn SQL_LEN_DATA_AT_EXEC verwendet wird, muss die Größe der Daten der Länge entsprechen, die Sie in SQL_LEN_DATA_AT_EXEC angegeben haben. Sie können SQL_DATA_AT_EXEC verwenden, aber der Einsatz von SQL_LEN_DATA_AT_EXEC bietet potenzielle Leistungsvorteile.|  
|Benutzerdefinierte Anwendungen, die die BCP API verwenden, können jetzt Warnungen anzeigen.|Die BCP API erzeugt jetzt für alle Typen Warnmeldungen, wenn die Datenlänge die angegebene Länge eines Felds überschreitet. Früher wurde diese Warnung nur für Zeichentypen ausgegeben, aber nicht für alle Typen.|  
|Wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wird, die an einen Datum-/Uhrzeit-Typ gebunden wurde, dann wird dadurch ein Fehler erzeugt.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 wurde kein Fehler erzeugt, wenn eine leere Zeichenfolge in eine **sql_variant**-Spalte eingefügt wurde, die an einen Datum-/Uhrzeit-Typ gebunden war. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 (und höher) generiert in dieser Situation ordnungsgemäß einen Fehler.|  
|Strengere SQL_C_TYPE _TIMESTAMP- und DBTYPE_DBTIMESTAMP-Parameterüberprüfung|Vor dem [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client wurden **DateTime** -Werte auf die Skala der Spalten **DateTime** und **smalldatetime** von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gerundet. 
  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (und höher) wendet jetzt die strengeren Validierungsregeln an, die in der ODBC-Hauptspezifikation für Sekundenbruchteile definiert sind. Wenn ein Parameterwert nicht mit den angegebenen oder vom Client implizierten Dezimalstellen in den SQL-Typ konvertiert werden kann, ohne dass nachfolgende Stellen abgeschnitten werden, dann wird ein Fehler zurückgegeben.|  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann andere Ergebnisse zurückgeben, wenn ein Trigger ausgeführt wird.|In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Änderungen können bewirken, dass für eine Anwendung andere Ergebnisse von einer Anweisung zurückgegeben werden, die die Ausführung eines Triggers verursachen, wenn **NOCOUNT OFF** gültig war. In dieser Situation kann die Anwendung einen Fehler generieren. Legen Sie zum Beheben dieses Fehlers **NOCOUNT ON** im-Befehl fest, oder nennen Sie SQLMoreResults, um zum nächsten Ergebnis zu gelangen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
