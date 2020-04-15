---
title: Microsoft Access-Datentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 024fb65b6fdc81ae0a8e007d1cee150c6a35b91c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307729"
---
# <a name="microsoft-access-data-types"></a>Microsoft Access-Datentypen
Die folgende Tabelle zeigt die Microsoft Access-Datentypen, die zum Erstellen von Tabellen verwendeten Datentypen und ODBC SQL-Datentypen.  
  
|Microsoft Access-Datentyp|Datentyp (CREATETABLE)|ODBC SQL-Datentyp|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY[1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|Zähler|Zähler|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|DATUM/UHRZEIT|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|LANGE BINÄR|LONGBINARY|SQL_LONGVARBINARY|  
|LONG TEXT|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|Memo|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|NUMBER (FieldSize= SINGLE)|Einzelnen|SQL_REAL|  
|NUMBER (FieldSize= DOUBLE)|Double|SQL_DOUBLE|  
|NUMBER (FieldSize= BYTE)|UNSIGNED BYTE|SQL_TINYINT|  
|NUMBER (FieldSize= INTEGER)|SHORT|SQL_SMALLINT|  
|NUMBER (FieldSize= LONG INTEGER)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR[1] SQL_WVARCHAR[2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] Greifen Sie nur auf 4.0-Anwendungen zu. Maximale Länge von 4000 Bytes. Verhalten ähnlich LONGBINARY.  
  
 [2] Nur ANSI-Anwendungen.  
  
 [3] Nur Unicode- und Access 4.0-Anwendungen.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-Datentypen zurück. Es werden nicht alle Microsoft Access-Datentypen zurückgegeben, wenn mehr als ein Microsoft Access-Typ demselben ODBC SQL-Datentyp zugeordnet ist. Alle Konvertierungen in Anhang D der *ODBC-Programmierreferenz* werden für die in der vorherigen Tabelle aufgeführten SQL-Datentypen unterstützt.  
  
 Die folgende Tabelle zeigt Einschränkungen für Microsoft Access-Datentypen.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|BINARY, VARBINARY und VARCHAR|Beim Erstellen einer BINARY-, VARBINARY- oder VARCHAR-Spalte mit Null oder nicht angegebener Länge wird tatsächlich eine 510-Byte-Spalte zurückgegeben.|  
|BYTE|Obwohl ein Microsoft Access NUMBER-Feld mit einer FieldSize gleich BYTE nicht signiert ist, kann bei Verwendung des Microsoft Access-Treibers eine negative Zahl in das Feld eingefügt werden.|  
|CHAR, LONGVARCHAR und VARCHAR|Ein Zeichenfolgenliteral kann ein beliebiges ANSI-Zeichen (1-255 dezimal) enthalten. Verwenden Sie zwei aufeinander folgende einfache Anführungszeichen ('), um ein einzelnes Anführungszeichen (') darzustellen.<br /><br /> Prozeduren sollten verwendet werden, um Zeichendaten zu übergeben, wenn ein Sonderzeichen in einer Zeichendatentypspalte verwendet wird.|  
|DATE|Datumswerte müssen entweder gemäß dem kanonischen Datumsformat ODBC oder durch das Datumstrennzeichen datumsabhängig (") begrenzt werden. Andernfalls behandelt Microsoft Access den Wert als arithmetischen Ausdruck und löst keine Warnung oder einen Fehler aus.<br /><br /> Beispielsweise muss das Datum "5. März 1996" als "d '1996-03-05'" oder #03/05/1996' dargestellt werden. Andernfalls wird Microsoft Access, wenn nur der 03.05.1993 eingereicht wird, dies als 3 dividiert durch 5 dividiert durch 1996 bewerten. Dieser Wert wird auf die ganze Zahl 0 aufgerunde, und da die Null-Tageskarte 1899-12-31, dies ist das verwendete Datum.<br /><br /> Ein Rohrzeichen (&#124;) kann nicht in einem Datumswert verwendet werden, auch wenn es in zurückgesetzte Anführungszeichen eingeschlossen ist.|  
|GUID|Datentyp, der auf Microsoft Access 4.0 beschränkt ist.|  
|NUMERIC|Datentyp, der auf Microsoft Access 4.0 beschränkt ist.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentypeinschränkungen](../../odbc/microsoft/data-type-limitations.md).
