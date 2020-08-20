---
description: Microsoft Excel-Datentypen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3e54ece7962fc5b56e4b9fcc17123ac7ad3c9e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466432"
---
# <a name="microsoft-excel-data-types"></a>Microsoft Excel-Datentypen
In der folgenden Tabelle wird gezeigt, wie Microsoft Excel-Treiber Datentypen ODBC-SQL-Datentypen zugeordnet werden. Der Microsoft Excel-Treiber weist diese Datentypen den Spalten in Microsoft Excel-Tabellen basierend auf den Daten in der Spalte zu.  
  
|Microsoft Excel-Datentyp|ODBC-Datentyp|  
|-------------------------------|--------------------|  
|WÄHRUNG|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|Richtig|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmier Referenz* werden für die zuvor in diesem Thema aufgeführten ODBC-SQL-Datentypen unterstützt.  
  
 In der folgenden Tabelle sind die Einschränkungen für Microsoft Excel-Datentypen aufgeführt.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Verschlüsselte Daten|Der Microsoft Excel-Treiber kann keine verschlüsselten Daten lesen.|  
|Fehler Zeichenfolgen|Der Microsoft Excel-Treiber kann eine Zeichenfolge für die Microsoft Excel-Fehler Werte (#N/a!, #Value!, #ref!, #DIV/0!, #Num!, #Name? und #null!) nicht zurückgeben, sondern stattdessen einen NULL-Wert zurückgeben.|  
|Richtig|Der Wert in einer logischen Spalte wird in einem SQL_C_CHAR Puffer entweder als 0 oder 1 zurückgegeben.|  
|NUMBER|Wenn eine ganzzahlige Spalte erstellt wird, können Zahlen, die für den ganzzahligen Datentyp zu groß sind, eingegeben werden, und Daten, die nicht ganzzahlige Werte enthalten, können eingefügt werden. das Ergebnis ist, dass die Spalte in SQL_DOUBLE konvertiert werden kann.|  
|TEXT|Wenn die Zeilen einer Spalte mehr als einen Microsoft Excel-Datentyp enthalten, weist der ODBC-Microsoft Excel-Treiber den SQL_VARCHAR-Datentyp der Spalte zu. Es gibt eine Ausnahme: Wenn die Spalte nur zwei oder drei der DateTime-Datentypen (Date, Time und DateTime) enthält, weist der ODBC-Microsoft Excel-Treiber den SQL_TIMESTAMP Datentyp der Spalte zu.<br /><br /> Beim Erstellen einer Text Spalte mit der Länge Null oder einer nicht angegebenen Länge wird tatsächlich eine 255-Byte-Spalte zurückgegeben.<br /><br /> Ein Zeichenfolgenliteralzeichen kann beliebige ANSI-Zeichen (1-255 Decimal) enthalten. Verwenden Sie zwei aufeinanderfolgende einfache Anführungszeichen ("), um ein einzelnes Anführungszeichen (') darzustellen.<br /><br /> Das Einfügen eines NULL-Werte in eine Spalte mit einem anderen Datentyp als SQL_VARCHAR bewirkt, dass der Datentyp der Spalte in SQL_VARCHAR geändert wird.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).
