---
title: Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen (OLE DB und ODBC) | Microsoft-Dokumentation
description: Erfahren Sie mehr zu den Datum-/Uhrzeiterweiterungen, die die Massenkopierfunktionalität im OLE DB-Treiber für SQL Server unterstützen.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, bulk copy operations
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 808454606f24ab397f5423edf901393ab3f7ccfa
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860238"
---
# <a name="bulk-copy-changes-for-enhanced-date-and-time-types-ole-db"></a>Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Artikel werden die Datum-/Uhrzeiterweiterungen beschrieben, die die Massenkopierfunktionalität im OLE DB-Treiber für SQL Server unterstützen.  
  
## <a name="format-files"></a>Formatdateien  
 Beim interaktiven Erstellen von Formatdateien beschreibt die folgende Tabelle die Eingaben, die zum Angeben von Datum-/Uhrzeittypen verwendet werden, sowie die entsprechenden Datentypnamen der Hostdatei.  
  
|Dateispeichertyp|Datentyp in der Hostdatei|Antwort auf die Eingabeaufforderung: „Geben Sie den Dateispeichertyp des Felds <Feldname> ein [\<default>]:“|  
|-----------------------|-------------------------|-----------------------------------------------------------------------------------------------------|  
|Datetime|SQLDATETIME|d|  
|Smalldatetime|SQLDATETIM4|D|  
|Date|SQLDATE|de|  
|Time|SQLTIME|te|  
|Datetime2|SQLDATETIME2|d2|  
|Datetimeoffset|SQLDATETIMEOFFSET|do|  
  
 Das XML-Formatdatei-XSD hat die folgenden Hinzufügungen:  
  
```  
<xs:complexType name="SQLDATETIME2">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATETIMEOFFSET">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATE">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLTIME">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
```  
  
## <a name="character-data-files"></a>Zeichendatendateien  
 In Zeichendatendateien werden Datums-und Uhrzeitwerte für OLE DB wie im Abschnitt „Datenformate: Zeichenfolgen und Literale“ unter [Data Type Support for OLE DB Date and Time Improvements (Datentypunterstützung für Verbesserungen von Datum und Uhrzeit in OLE DB)](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md) beschrieben dargestellt.  
  
 In nativen Datendateien werden Datums- und Uhrzeitwerte für die vier neuen Typen als TDS-Entsprechungen mit sieben Dezimalstellen dargestellt, da es sich dabei um das von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützte Maximum handelt und bcp-Datendateien die Dezimalstellen dieser Spalten nicht speichern. Es erfolgt keine Änderung an der Speicherung der vorhandenen **datetime**- und **smalldatetime**-Typen oder ihrer Tabular Data Stream-Entsprechungen (TDS).  
  
 Die Speichergrößen für die anderen Speichertypen sind für OLE DB wie folgt:  
  
|Dateispeichertyp|Speichergröße (in Byte)|  
|-----------------------|---------------------------|  
|datetime|8|  
|smalldatetime|4|  
|date|3|  
|time|6|  
|datetime2|9|  
|datetimeoffset|11|  
 
  
## <a name="bcp-types-in-msoledbsqlh"></a>BCP-Typen in msoledbsql.h  
 Die folgenden Typen werden in msoledbsql.h definiert. Diese Typen werden mit dem Parameter *eUserDataType* von IBCPSession::BCPColFmt in OLE DB übergeben.  
  
|Dateispeichertyp|Datentyp in der Hostdatei|Für die Verwendung mit IBCPSession::BCPColFmt in msoledbsql.h einzugeben|Wert|  
|-----------------------|-------------------------|-----------------------------------------------------------|-----------|  
|Datetime|SQLDATETIME|BCP_TYPE_SQLDATETIME|0x3d|  
|Smalldatetime|SQLDATETIM4|BCP_TYPE_SQLDATETIM4|0x3a|  
|Date|SQLDATE|BCP_TYPE_SQLDATE|0x28|  
|Time|SQLTIME|BCP_TYPE_SQLTIME|0x29|  
|Datetime2|SQLDATETIME2|BCP_TYPE_SQLDATETIME2|0x2a|  
|Datetimeoffset|SQLDATETIMEOFFSET|BCP_TYPE_SQLDATETIMEOFFSET|0x2b|  
  
## <a name="bcp-data-type-conversions"></a>BCP-Datentypkonvertierungen  
 Die folgenden Tabellen enthalten Konvertierungsinformationen.  
  
 **OLE DB-Hinweis** Die folgenden Konvertierungen werden von IBCPSession ausgeführt. IRowsetFastLoad nutzt OLE DB-Konvertierungen gemäß der Definition unter [Konvertierungen von Client zu Server](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md). Beachten Sie, dass datetime-Werte auf 1/300stel einer Sekunde gerundet werden und dass für smalldatetime-Werte die Sekunden vom Server auf null festgelegt werden, nachdem die unten beschriebenen Clientkonvertierungen durchgeführt wurden. Datetime-Rundung wird durch Stunden und Minuten, aber nicht durch das Datum weitergegeben.  
  
|Bis --><br /><br /> From|date|time|smalldatetime|datetime|datetime2|datetimeoffset|char|wchar|  
|------------------------|----------|----------|-------------------|--------------|---------------|--------------------|----------|-----------|  
|Date|1|-|1, 6|1, 6|1, 6|1, 5, 6|1, 3|1, 3|  
|Time|–|1, 10|1, 7, 10|1, 7, 10|1, 7, 10|1, 5, 7, 10|1, 3|1, 3|  
|Smalldatetime|1, 2|1, 4, 10|1|1|1, 10|1, 5, 10|1, 11|1, 11|  
|Datetime|1, 2|1, 4, 10|1, 12|1|1, 10|1, 5, 10|1, 11|1, 11|  
|Datetime2|1, 2|1, 4, 10|1, 12|1, 10|1, 10|1, 5, 10|1, 3|1, 3|  
|Datetimeoffset|1, 2, 8|1, 4, 8, 10|1, 8, 10|1, 8, 10|1, 8, 10|1, 10|1, 3|1, 3|  
|Char/wchar (date)|9|-|9, 6, 12|9, 6, 12|9, 6|9, 5, 6|–|–|  
|Char/wchar (time)|-|9, 10|9, 7, 10, 12|9, 7, 10, 12|9, 7, 10|9, 5, 7, 10|–|–|  
|Char/wchar (datetime)|9, 2|9, 4, 10|9, 10, 12|9, 10, 12|9, 10|9, 5, 10|–|–|  
|Char/wchar (datetimeoffset)|9, 2, 8|9, 4, 8, 10|9, 8, 10, 12|9, 8, 10, 12|9, 8, 10|9, 10|–|–|  
  
#### <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|-|Es wird keine Konvertierung unterstützt.<br />|  
|1|Wenn die angegebenen Daten nicht gültig sind, wird ein Fehler ausgegeben. Für datetimeoffset-Werte muss der Uhrzeitteil nach der Konvertierung in das UTC-Format innerhalb des gültigen Bereichs liegen, und zwar selbst dann, wenn keine Konvertierung in UTC angefordert wird. Das liegt daran, dass TDS und der Server immer die Uhrzeit in datetimeoffset-Werten für UTC normalisieren. Darum muss der Client überprüfen, dass sich die Zeitkomponenten innerhalb des nach Konvertierung zu UTC unterstützten Bereichs befinden.|  
|2|Die Uhrzeitkomponente wird ignoriert.|  
|3|Wenn eine Kürzung mit Datenverlust auftritt, wird ein Fehler generiert. Für „datetime2“ wird die Anzahl der Dezimalstellen für Sekundenbruchteile anhand der Größe der Zielspalte gemäß der folgenden Tabelle bestimmt: Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von OLE&nbsp;DB zugelassene Maximum.<br /><br /> **Typ:** DBTIME2<br /><br /> **Implizierte Dezimalstellen 0** 8<br /><br /> **Implizierte Dezimalstellen 1..9**1..9<br /><br /> <br /><br /> **Typ:** DBTIMESTAMP<br /><br /> **Implizierte Dezimalstellen 0:** 19<br /><br /> **Implizierte Dezimalstellen 1..9:** 21..29<br /><br /> <br /><br /> **Typ:** DBTIMESTAMPOFFSET<br /><br /> **Implizierte Dezimalstellen 0:** 26<br /><br /> **Implizierte Dezimalstellen 1..9:** 28..36|  
|4|Die Datumskomponente wird ignoriert.|  
|5|Die Zeitzone wird auf UTC festgelegt (zum Beispiel 00:00).|  
|6|Die Uhrzeit wird auf 0 (Null) festgelegt.|  
|7|Das Datum wird auf den 01.01.1900 festgelegt.|  
|8|Der Zeitzonenoffset wird ignoriert.|  
|9|Die Zeichenfolge wird analysiert und je nach dem ersten Satzzeichen und dem Vorhandensein weiterer Komponenten in einen date-, datetime-, datetimeoffset- oder time-Wert konvertiert. Die Zeichenfolge wird dann in den Zieltyp konvertiert. Dabei wird nach den Regeln am Ende dieses Artikels für den Quelltyp vorgegangen, der von diesem Prozess ermittelt wird. Wenn die bereitgestellten Daten nicht analysiert werden können, ohne einen Fehler auszulösen, wenn sich ein Komponententeil außerhalb des zulässigen Bereichs befindet oder wenn keine Konvertierung vom Literaltyp zum Zieltyp stattfindet, wird ein Fehler ausgegeben. Bei den datetime- und smalldatetime-Parametern wird ein Fehler ausgegeben, wenn sich das Jahr außerhalb des von diesen Typen unterstützen Bereichs befindet.<br /><br /> Der Wert für datetimeoffset muss nach der Konvertierung in das UTC-Format innerhalb des gültigen Bereichs liegen und zwar selbst dann, wenn keine Konvertierung in UTC angefordert wird. Der Grund dafür ist, dass der TDS und der Server das Datum stets in datetimeoffset-Werte für UTC normalisieren, weshalb der Client prüfen muss, ob die Zeitkomponenten innerhalb des nach Konvertierung in UTC unterstützten Bereichs liegen. Wenn der Wert sich nicht im unterstützten UTC-Bereich befindet, wird ein Fehler ausgegeben.|  
|10|Für Konvertierungen von Client zu Server wird ein Fehler generiert, wenn eine Kürzung mit Datenverlust auftritt. Dieser Fehler tritt auch dann auf, wenn der Wert außerhalb des Bereichs liegt, der vom UTC-Bereich, den der Server verwendet, dargestellt werden kann. Wenn während einer Konvertierung vom Server zum Client eine Kürzung der Sekunden oder Sekundenbruchteile auftritt, wird lediglich eine Warnung angezeigt.|  
|11|Für Konvertierungen von Client zu Server wird ein Fehler generiert, wenn eine Kürzung mit Datenverlust auftritt.|
|12|Die Sekunden werden auf null festgelegt, und die Sekundenbruchteile werden verworfen. Kein Kürzungsfehler ist möglich.|  
|–|Das Verhalten von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und früheren Versionen ist beibehalten worden.|  
  
## <a name="see-also"></a>Weitere Informationen     
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
