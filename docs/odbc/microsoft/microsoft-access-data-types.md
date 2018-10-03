---
title: Microsoft Access-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11f45698a5ad8b7fd05052cbb2d23520790c425a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692978"
---
# <a name="microsoft-access-data-types"></a>Microsoft Access-Datentypen
Die folgende Tabelle zeigt die Microsoft Access-Datentypen, Datentypen, die zum Erstellen von Tabellen verwendet, und ODBC-SQL-Datentypen.  
  
|Microsoft Access-Datentyp|-Datentyp (CREATETABLE)|ODBC-SQL-Datentyp|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|LEISTUNGSINDIKATOR|LEISTUNGSINDIKATOR|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|DATUM/UHRZEIT|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|LANGE BINÄRDATEI|LONGBINARY|SQL_LONGVARBINARY|  
|LANGER TEXT|LONGTEXT|SQL_WLONGVARCHAR FÜR SQL_LONGVARCHAR [2] [3]|  
|MEMO|LONGTEXT|SQL_WLONGVARCHAR FÜR SQL_LONGVARCHAR [2] [3]|  
|Anzahl (Feldgröße = SINGLE)|EINZELNE|SQL_REAL|  
|Anzahl (Feldgröße = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|Anzahl (Feldgröße = BYTE)|BYTE OHNE VORZEICHEN|SQL_TINYINT|  
|Anzahl (Feldgröße = ganze Zahl)|KURZE|SQL_SMALLINT|  
|Anzahl (Feldgröße = LONG Integer-Wert)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|[1]-SQL_VARCHAR, SQL_WVARCHAR [2]|  
ARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] auf nur 4.0-Anwendungen sind. Maximale Länge von 4.000 Byte. Verhalten LONGBINARY ähnelt.  
  
 [2] nur für-ANSI-Anwendungen.  
  
 [3] nur für Unicode-"und" Access 4.0-Anwendungen.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC-Datentypen zurückgegeben. Es wird nicht alle Microsoft Access-Datentypen zurückgegeben, wenn mehr als eine Microsoft Access-Typ in den gleichen ODBC-SQL-Datentyp zugeordnet ist. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden für die SQL-Datentypen, die in der vorherigen Tabelle aufgeführten unterstützt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Microsoft Access-Datentypen.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY und VARCHAR|Erstellen einer BINARY, VARBINARY und VARCHAR-Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 510-Byte-Spalte zurück.|  
|BYTE|Auch, wenn ein Feld für die Microsoft Access Zahl mit einem BYTE gleich Feldgröße nicht signiert ist, kann eine negative Zahl in das Feld eingefügt werden, wenn der Microsoft Access-Treiber verwendet.|  
|CHAR, VARCHAR und LONGVARCHAR|Ein Zeichenfolgenliteral kann ANSI-Zeichen (1 bis 255 dezimal) enthalten. Verwenden Sie zwei aufeinander folgende einfache Anführungszeichen ("), um ein einfaches Anführungszeichen (') darzustellen.<br /><br /> Verfahren sollte verwendet werden, um Zeichendaten zu übergeben, bei Verwendung von Sonderzeichen in einem Zeichen-Datentypspalte.|  
|DATE|Date-Werte müssen werden gemäß der kanonischen ODBC-Datumsformat getrennt oder durch das Trennzeichen "DateTime" ("#") getrennt. Andernfalls, Microsoft Access wird der Wert wird als ein arithmetischer Ausdruck behandelt und löst keine Warnung oder einen Fehler.<br /><br /> Z. B. das Datum "5. März 1996" muss, als dargestellt werden {d ' 1996-03-05 "} oder #03/05/1996 #; andernfalls nur 03/05/1993 gesendet wird, wird Microsoft Access dies als 3 geteilt durch 5 geteilt durch 1996 ausgewertet. Dieser Wert wird aufgerundet, um die ganze Zahl 0, und da 1899-12-31 der 0 (null) Tag zugeordnet ist, ist dies das Datum verwendet.<br /><br /> Einem senkrechten Strich (&#124;) kann nicht in einen Datumswert verwendet werden, auch wenn es wieder in Anführungszeichen eingeschlossen.|  
|GUID|Der Datentyp auf der Microsoft Access 4.0 beschränkt.|  
|NUMERIC|Der Datentyp auf der Microsoft Access 4.0 beschränkt.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
