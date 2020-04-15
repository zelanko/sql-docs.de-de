---
title: Microsoft Excel-Datentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8574985e10e5aaa3ae5431af7ee1245643e20b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283770"
---
# <a name="microsoft-excel-data-types"></a>Microsoft Excel-Datentypen
Die folgende Tabelle zeigt, wie Microsoft Excel-Treiberdatentypen ODBC SQL-Datentypen zugeordnet werden. Der Microsoft Excel-Treiber weist diese Datentypen Spalten in Microsoft Excel-Tabellen basierend auf den Daten in der Spalte zu.  
  
|Microsoft Excel-Datentyp|ODBC-Datentyp|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|Logische|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmierreferenz* werden für die ODBC SQL-Datentypen unterstützt, die weiter oben in diesem Thema aufgeführt sind.  
  
 Die folgende Tabelle zeigt Einschränkungen für Microsoft Excel-Datentypen.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Verschlüsselte Daten|Der Microsoft Excel-Treiber kann keine verschlüsselten Daten lesen.|  
|Fehlerzeichenfolgen|Der Microsoft Excel-Treiber kann keine Zeichenfolge für die Microsoft Excel-Fehlerwerte (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?und #NULL!) zurückgeben, sondern stattdessen null zurück.|  
|Logische|Der Wert in einer LOGICAL-Spalte wird in einem SQL_C_CHAR-Puffer als 0 oder 1 zurückgegeben.|  
|NUMBER|Wenn eine Ganzzahlspalte erstellt wird, können Zahlen eingegeben werden, die für den Ganzzahldatentyp zu groß sind, und Daten, die Nicht-Ganzzahlwerte enthalten, können eingefügt werden, sodass die Spalte in SQL_DOUBLE konvertiert werden kann.|  
|TEXT|Wenn die Zeilen einer Spalte mehr als einen Microsoft Excel-Datentyp enthalten, weist der ODBC Microsoft Excel-Treiber der Spalte den SQL_VARCHAR Datentyp zu. Es gibt eine Ausnahme: Wenn die Spalte nur zwei oder drei der Datetime-Datentypen (DATE, TIME und DATETIME) enthält, weist der ODBC Microsoft Excel-Treiber der Spalte den SQL_TIMESTAMP Datentyp zu.<br /><br /> Beim Erstellen einer TEXT-Spalte mit null oder nicht angegebener Länge wird tatsächlich eine 255-Byte-Spalte zurückgegeben.<br /><br /> Ein Zeichenfolgenliteral kann ein beliebiges ANSI-Zeichen (1-255 dezimal) enthalten. Verwenden Sie zwei aufeinander folgende einfache Anführungszeichen ("), um ein einzelnes Anführungszeichen (') darzustellen.<br /><br /> Das Einfügen eines NULL-Werts in eine Spalte mit einem anderen Datentyp als SQL_VARCHAR führt dazu, dass sich der Datentyp der Spalte in SQL_VARCHAR ändert.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentypeinschränkungen](../../odbc/microsoft/data-type-limitations.md).
