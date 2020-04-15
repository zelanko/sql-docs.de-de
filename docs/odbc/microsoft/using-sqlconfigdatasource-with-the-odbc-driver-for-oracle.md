---
title: Verwenden von SQLConfigDatasource mit dem ODBC-Treiber für Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 718e444d63e0d4cf3821c0c03eb851732ed5b4e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292770"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Verwenden von SQLConfigDatasource mit dem ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In der folgenden Tabelle sind gültige **SQLConfigDatasource-Einstellungen** für den Microsoft ODBC-Treiber für Oracle, Version 1.0 (Msorcl10.dll) und der Microsoft ODBC-Treiber für Oracle, Version 2.0 (Msorcl32.dll) aufgeführt.  
  
> [!NOTE]  
>  Der Treiber Msorcl10.dll (Version 1.0) unterstützt alle Einstellungen außer **Server**. Der Treiber Msorcl32.dll (Version 2.0 und höher) unterstützt alle Einstellungen.  
  
 Einige Einstellungen werden vom Treiber ignoriert, aber von **SQLConfigDatasource**akzeptiert. Die Aufnahme dieser Einstellungen in die ODBC-Verbindungszeichenfolge ist die einzige Möglichkeit, wie sie zur Laufzeit akzeptiert werden. Eine ignorierte Einstellung wird nicht in der Registrierung gespeichert, wenn **SQLConfigDatasource** die Datenquelle erstellt.  
  
 In der folgenden Tabelle bedeutet *A/N* jede gültige alphanumerische Zeichenfolge bis zur maximal zulässigen Länge. *Max Len* (maximale Länge) ist die maximal zulässige Zeichenfolgenlänge, die von der Einstellung akzeptiert wird, einschließlich des Zeichenfolgen-Terminator-Zeichens.  
  
|Einstellung|Max Len|Standardwert|Gültige Werte|Beschreibung|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65.535|1000|Minimale Abrufpuffergröße bis zu 65535 Bytes|  
|CatalogCap|2|1|0 oder 1|Wenn 1, werden nicht zitierte Bezeichner in großbuchstaben in den Katalogfunktionen konvertiert.|  
|ConnectString|128|""|A/N|Verbindungszeichenfolge. Erforderliche Methode zum Angeben des Servernamens mit dem Treiber Msorcl10.dll.|  
|Beschreibung|256|""|A/N|Beschreibung|  
|DSN|33|""|A/N|Datenquellenname.|  
|GuessTheColDef|4|0|A/N|Gibt einen Wert ungleich Null für Spalten ohne Oracle-definierten Maßstab zurück.|  
|NumberFloat|2|""|0 oder 1|Wenn 0, werden FLOAT-Spalten als SQL_FLOAT behandelt. Wenn 1, werden FLOAT-Spalten als SQL_DOUBLE behandelt.|  
|PWD|30|""|A/N|Password:|  
|RDOSupport|2|""|0 oder 1|Ermöglicht RDO das Aufrufen von Oracle-Prozeduren.|  
|Bemerkungen|2|0|0 oder 1|Fügen Sie REMARKS in Katalogfunktionen ein.|  
|RowLimit|4|""|0 bis 99|Maximale Anzahl von Zeilen, die von einer SELECT-Anweisung zurückgegeben werden. Eine Zeichenfolge mit einer Länge von Null gibt an, dass kein Grenzwert angewendet wird.|  
|Server|128|""|A/N|Oracle-Servername.|  
|SynonymColumns|2|1|0 oder 1|Schließen Sie SYNONYMs in SQLColumns ein.|  
|SystemTabelle|2|""|0 oder 1|Wenn 0, werden keine Systemtabellen angezeigt. Wenn 1, werden Systemtabellen angezeigt.|  
|ÜbersetzungDLL|33|""|A/N|Übersetzung .dll Name.|  
|TranslationName|33|""|A/N|Übersetzungsname.|  
|TranslationOption|33|""|A/N|Übersetzungsoption.|  
|TxnCap|2|""|A/N|Transaktionsfähig. Wenn 0, meldet der Treiber, dass er keine Transaktionen unterstützt. Wenn 1, meldet der Treiber, dass er in der Lage ist, Transaktionen auszuführen.|  
|UID|30|""|A/N|Benutzername.|
