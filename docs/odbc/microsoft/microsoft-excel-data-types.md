---
title: Microsoft Excel-Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a8385c8efb1ab7dcee651e5acb52062292a0bcc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045024"
---
# <a name="microsoft-excel-data-types"></a>Microsoft Excel-Datentypen
Die folgende Tabelle zeigt, wie Microsoft Excel-Treiber-Datentypen in ODBC-SQL-Datentypen zugeordnet werden. Microsoft Excel-Treibers weist diese Datentypen für Spalten in Microsoft Excel-Tabellen, die basierend auf den Daten in der Spalte an.  
  
|Microsoft Excel-Datentyp|ODBC-Datentyp|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|LOGISCHE|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt der ODBC-SQL-Datentypen. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden unterstützt, für die ODBC-SQL-Datentypen, die weiter oben in diesem Thema aufgeführt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Microsoft Excel-Datentypen.  
  
|Datentyp|Beschreibung|  
|---------------|-----------------|  
|Verschlüsselte Daten|Der Microsoft Excel-Treiber kann nicht auf verschlüsselte Daten gelesen.|  
|Fehlerzeichenfolgen|Der Microsoft Excel-Treiber kann keine Zeichenfolge für die Microsoft Excel-Fehlerwerte zurück (#n!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, und #NULL!), sondern stattdessen eine NULL zurück.|  
|LOGISCHE|Der Wert in eine logische Spalte wird in einem Puffer werden als 0 oder 1 zurückgegeben.|  
|NUMBER|Wenn eine Spalte mit ganzen Zahlen erstellt wurde, Zahlen, die zu groß für den Integer-Datentyp sind, können eingegeben werden, und Daten, die nicht ganzzahlige Werte eingefügt werden können, mit dem Ergebnis, dass die Spalte in SQL_DOUBLE konvertiert werden kann.|  
|TEXT|Wenn die Zeilen einer Spalte mehr als einen Typ von Microsoft Excel-Daten enthalten, weist der Treiber ODBC Microsoft Excel den SQL_VARCHAR-Datentyp der Spalte an. Es wird eine Ausnahme: enthält die Spalte nur zwei oder drei der Datetime-Datentypen (DATE, TIME und DATETIME), weist der Treiber ODBC Microsoft Excel der SQL_TIMESTAMP-Datentyp der Spalte.<br /><br /> Erstellen eine Textspalte mit 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 255-Byte-Spalte zurück.<br /><br /> Ein Zeichenfolgenliteral kann ANSI-Zeichen (1 bis 255 dezimal) enthalten. Verwenden Sie zwei aufeinander folgende einfache Anführungszeichen ("), um ein einfaches Anführungszeichen (') darzustellen.<br /><br /> Einfügen von NULL in eine Spalte mit einem anderen Datentyp als SQL_VARCHAR führt dazu, dass den Datentyp der Spalte, die in SQL_VARCHAR zu ändern.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
