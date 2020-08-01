---
title: Client-/Server-Konvertierungen
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], client to server
ms.assetid: 6bb24928-0f3e-4119-beda-cfd04a44a3eb
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da80b44c2b24d58906d4b8fab6c0989caceec544
ms.sourcegitcommit: 4b775a3ce453b757c7435cc2a4c9b35d0c5a8a9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87472266"
---
# <a name="sql-server-native-client-conversions-performed-from-client-to-server"></a>SQL Server Native Client vom Client zum Server durchgeführte Konvertierungen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Dieses Thema beschreibt die Datums-/Uhrzeit-Konvertierungen zwischen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE&nbsp;DB und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) entwickelten Clientanwendungen.  
  
## <a name="conversions"></a>Konvertierungen  
 In diesem Thema werden die auf dem Client durchgeführten Konvertierungen beschrieben. Wenn der Client Bruchsekundengenauigkeit für einen Parameter angibt, die von der auf dem Server definierten abweicht, schlägt die Clientkonvertierung in Fällen, in denen der Server eine erfolgreiche Konvertierung zugelassen hätte, möglicherweise fehl. Insbesondere behandelt der Client jedes Abschneiden von Sekundenbruchteilen als Fehler, wohingegen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeitwerte auf die nächste ganze Sekunde rundet.  
  
 Wenn „ICommandWithParameters::SetParameterInfo“ nicht aufgerufen wird, werden DBTYPE_DBTIMESTAMP-Bindungen als **datetime2** konvertiert.  
  
|Bis --><br /><br /> From|DBDATE (date)|DBTIME (time)|DBTIME2 (time)|DBTIMESTAMP (smalldatetime)|DBTIMESTAMP (datetime)|DBTIMESTAMP (datetime2)|DBTIMESTAMPOFFSET (datetimeoffset)|STR|WSTR|SQLVARIANT<br /><br /> (sql_variant)|  
|----------------------|---------------------|---------------------|----------------------|-----------------------------------|------------------------------|-------------------------------|------------------------------------------|---------|----------|-------------------------------------|  
|DATE|1,2|1,3,4|4,12|1,12|1,12|1,12|1,5, 12|1,12|1,12|1,12<br /><br /> datetime2(0)|  
|DBDATE|1|-|-|1,6|1,6|1,6|1,5, 6|1,10|1,10|1<br /><br /> date|  
|DBTIME|-|1|1|1,7|1,7|1,7|1,5, 7|1,10|1,10|1<br /><br /> Time(0)|  
|DBTIME2|-|1,3|1|1,7,10,14|1,7,10,15|1,7,10|1,5,7,10|1,10,11|1,10,11|1<br /><br /> Time(7)|  
|DBTIMESTAMP|1,2|1,3,4|1,4,10|1,10,14|1,10,15|1,10|1,5,10|1,10,11|1,10,11|1,10<br /><br /> datetime2(7)|  
|DBTIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10,14|1,8,10,15|1,8,10|1,10|1,10,11|1,10,11|1,10<br /><br /> datetimeoffset(7)|  
|FILETIME|1,2|1,3,4|1,4,13|1,13|1,13|1,13|1,5,13|1,13|1,10|1,13<br /><br /> datetime2(3)|  
|BYTES|-|-|-|-|-|-|-|N/V|–|–|  
|VARIANT|1|1|1|1,10|1,10|1,10|1,10|N/V|–|1,10|  
|SSVARIANT|1,16|1,16|1,16|1,10,16|1,10,16|1,10,16|1,10,16|N/V|–|1,16|  
|BSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|N/V|–|–|  
|STR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|N/V|–|–|  
|WSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|N/V|–|–|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|-|Es wird keine Konvertierung unterstützt. Wenn beim Aufruf von IAccessor::CreateAccessor die Bindung überprüft wird, wird DBBINDSTATUS_UPSUPPORTEDCONVERSION in *rgStatus* zurückgegeben. Bei Verzögerung der Accessorüberprüfung wird DBSTATUS_E_BADACCESSOR festgelegt.|  
|N/V|Nicht zutreffend.|  
|1|Wenn die bereitgestellten Daten nicht gültig sind, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Die Eingabedaten werden überprüft, bevor die Konvertierungen angewendet werden, d. h. auch wenn eine Komponente von einer nachfolgenden Konvertierung ignoriert wird, muss sie gültig sein, damit die Konvertierung ordnungsgemäß durchgeführt werden kann.|  
|2|Zeitfelder werden ignoriert.|  
|3|Sekundenbruchteile müssen 0 sein, oder es wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|4|Die Datumskomponente wird ignoriert.|  
|5|Die Zeitzone wird auf die Zeitzone des Clients festgelegt.|  
|6|Die Uhrzeit wird auf 0 (Null) festgelegt.|  
|7|Das Datum wird auf das aktuelle Datum festgelegt.|  
|8|Die Zeit wird zu UTC konvertiert. Wenn während dieser Konvertierung ein Fehler auftritt, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt.|  
|9|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert.<br /><br /> Wenn der Zieltyp „DBTIMESTAMP“, **smalldatetime**, **datetime** oder **datetime2** ist, muss die Zeichenfolge mit der Syntax für Datums-, Uhrzeit- oder **datetime2**-Literalen oder der von OLE erkannten Syntax konform sein. Wenn die Zeichenfolge ein Datumsliteral ist, werden alle Uhrzeitkomponenten auf 0 festgelegt. Wenn die Zeichenfolge ein Uhrzeitliteral ist, wird das Datum auf das aktuelle Datum festgelegt.<br /><br /> Für alle anderen Zieltypen muss die Zeichenfolge der Syntax für Literale des Zieltyps entsprechen.|  
|10|Wenn das Abschneiden von Sekundenbruchteilen Datenverlust verursacht, wird DBSTATUS_E_DATAOVERFLOW festgelegt. Für Zeichenfolgenkonvertierungen ist eine Überlaufprüfung nur möglich, wenn die Zeichenfolge der ISO-Syntax entspricht. Wenn es sich bei der Zeichenfolge um ein OLE-Datumsliteral handelt, werden Sekundenbruchteile gerundet.<br /><br /> Bei der Konvertierung von DBTIMESTAMP (DateTime) zu smalldatetime [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird Native Client den Sekundenwert automatisch abgeschnitten, anstatt den DBSTATUS_E_DATAOVERFLOW Fehler zu erhöhen.|  
|11|Die Anzahl der Dezimalziffern für Sekundenbruchteile (Dezimalstellen) wird anhand der Größe der Zielspalte gemäß der folgenden Tabelle ermittelt. Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von OLE&nbsp;DB zugelassene Maximum.<br /><br /> Wenn jedoch der Quelltyp DBTIMESTAMP ist, und Sekundenbruchteile auf 0 gesetzt wurden, werden keine Dezimalstellen für Sekundenbruchteile und kein Dezimaltrennzeichen generiert. Dieses Verhalten stellt die Abwärtskompatibilität für Anwendungen sicher, die mit älteren OLE DB-Anbietern entwickelt wurden.<br /><br /> Eine Spaltengröße von ~0 impliziert unbegrenzte Größe in OLE&nbsp;DB (9 Ziffern, sofern nicht die 3-Ziffern-Regel für DBTIMESTAMP gilt).|  
|12|Die in Vorgängerversionen von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] gültige Konvertierungssemantik für DBTYPE_DATE wird beibehalten. Die Sekundenbruchteile werden zu&nbsp;0 abgeschnitten.|  
|13|Die in Vorgängerversionen von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] gültige Konvertierungssemantik für DBTYPE_FILETIME wird beibehalten. Wenn Sie die Windows-FileTimeToSystemTime-API verwenden, ist die Genauigkeit für Sekundenbruchteile auf eine Millisekunde beschränkt.|  
|14|Die in Vorgängerversionen von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] gültige Konvertierungssemantik für **smalldatetime** wird beibehalten. Die Sekunden werden auf&nbsp;0 festgelegt.|  
|15|Die in Vorgängerversionen von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] gültige Konvertierungssemantik für **datetime** wird beibehalten. Sekunden werden zum nächstem 300stel einer Sekunde gerundet.|  
|16|Das Konvertierungsverhalten eines in eine SSVARIANT-Clientstruktur eingebetteten Werts (eines bestimmten Typs) ist mit dem Verhalten desselben Werts und Typs identisch, wenn er nicht eingebettet ist.|  
  
|type|Länge (in Zeichen)|Skalieren|  
|-|-|-|  
|DBTIME2|8, 10..18|0,1..9|  
|DBTIMESTAMP|19, 21..29|0,1..9|  
|DBTIMESTAMPOFFSET|26, 28...36|0,1..9|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
  
  
