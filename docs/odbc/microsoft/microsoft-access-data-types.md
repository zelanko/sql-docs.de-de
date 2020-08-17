---
description: Microsoft Access-Datentypen
title: Microsoft Access-Datentypen | Microsoft-Dokumentation
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
ms.openlocfilehash: 24428c436e9e60c8ca5e42288b217f2c576cbd0d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340766"
---
# <a name="microsoft-access-data-types"></a>Microsoft Access-Datentypen
In der folgenden Tabelle werden die Microsoft Access-Datentypen, Datentypen zum Erstellen von Tabellen und ODBC-SQL-Datentypen angezeigt.  
  
|Microsoft Access-Datentyp|Datentyp (kreatetable)|ODBC SQL-Datentyp|  
|--------------------------------|-------------------------------|------------------------|  
|Bigbinary [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|Indikator|Indikator|SQL_INTEGER|  
|WÄHRUNG|WÄHRUNG|SQL_NUMERIC|  
|Datum/Uhrzeit|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|lange Binärdatei|LONGBINARY|SQL_LONGVARBINARY|  
|langer Text|LONGTEXT|SQL_LONGVARCHAR [2] SQL_WLONGVARCHAR [3]|  
|Anruf|LONGTEXT|SQL_LONGVARCHAR [2] SQL_WLONGVARCHAR [3]|  
|Number (FieldSize = Single)|Gänger|SQL_REAL|  
|Number (FieldSize = Double)|Double|SQL_DOUBLE|  
|Number (FieldSize = Byte)|Byte ohne Vorzeichen|SQL_TINYINT|  
|Number (FieldSize = Integer)|SHORT|SQL_SMALLINT|  
|Number (FieldSize = Long Integer)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR [1] SQL_WVARCHAR [2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] nur auf 4,0-Anwendungen zugreifen. Maximale Länge von 4000 bytes. Ähnliches Verhalten wie LONGBINARY.  
  
 [2] nur ANSI-Anwendungen.  
  
 [3] nur Unicode-und Access 4,0-Anwendungen.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-Datentypen zurück. Es werden nicht alle Microsoft Access-Datentypen zurückgegeben, wenn dem gleichen ODBC-SQL-Datentyp mehr als ein Microsoft-Zugriffstyp zugeordnet ist. Alle Konvertierungen in Anhang D der *ODBC-Programmier Referenz* werden für die SQL-Datentypen unterstützt, die in der vorherigen Tabelle aufgeführt sind.  
  
 In der folgenden Tabelle sind die Einschränkungen für Microsoft Access-Datentypen aufgeführt.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Binary, varbinary und varchar|Beim Erstellen einer Spalte vom Typ binary, varbinary oder varchar mit 0 (null) oder einer nicht angegebenen Länge wird tatsächlich eine 510-Byte-Spalte zurückgegeben.|  
|BYTE|Obwohl ein Microsoft-Zugriffs Nummern Feld mit einem FieldSize-Wert von Byte nicht signiert ist, kann bei Verwendung des Microsoft Access-Treibers eine negative Zahl in das Feld eingefügt werden.|  
|Char, LONGVARCHAR und varchar|Ein Zeichenfolgenliteralzeichen kann beliebige ANSI-Zeichen (1-255 Decimal) enthalten. Verwenden Sie zwei aufeinanderfolgende einfache Anführungszeichen (' '), um ein einzelnes Anführungszeichen (') darzustellen.<br /><br /> Prozeduren sollten verwendet werden, um Zeichendaten bei Verwendung eines beliebigen Sonderzeichens in einer Zeichen Datentyp Spalte zu übergeben.|  
|DATE|Datumswerte müssen entweder entsprechend dem kanonischen ODBC-Datumsformat begrenzt oder durch das DateTime-Trennzeichen ("#") getrennt werden. Andernfalls wird der Wert von Microsoft Access als arithmetischer Ausdruck behandelt, und es wird keine Warnung oder ein Fehler ausgegeben.<br /><br /> Beispielsweise muss das Datum "5. März 1996" als {d ' 1996-03-05 '} oder #03/05/1996 #; dargestellt werden. Wenn nur 03/05/1993 übermittelt wird, wertet Microsoft Access dies als 3 dividiert durch 5 dividiert durch 1996 aus. Dieser Wert wird auf die Ganzzahl 0 aufgerundet, und da der Zero-Tag 1899-12-31 zugeordnet ist, ist dies das verwendete Datum.<br /><br /> Ein senkrechter Strich (&#124;) kann nicht in einem Datumswert verwendet werden, auch wenn er in backanführungs Zeichen eingeschlossen ist.|  
|GUID|Der Datentyp ist auf Microsoft Access 4,0 beschränkt.|  
|NUMERIC|Der Datentyp ist auf Microsoft Access 4,0 beschränkt.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).
