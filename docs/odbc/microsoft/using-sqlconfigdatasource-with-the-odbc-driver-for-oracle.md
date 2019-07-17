---
title: Verwenden von SQLConfigDatasource mit dem ODBC-Treiber für Oracle | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa5f1ecf9f3100480081e3744fc7d280a4da282b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088035"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Verwenden von SQLConfigDatasource mit dem ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Die folgende Tabelle enthält, die gültige **SQLConfigDatasource** Einstellungen für Microsoft ODBC-Treiber für Oracle, Version 1.0 (Msorcl10.dll) und Microsoft ODBC-Treiber für Oracle, Version 2.0 (Msorcl32.dll).  
  
> [!NOTE]  
>  Der Msorcl10.dll-Treiber (Version 1.0) unterstützt alle Einstellungen, mit Ausnahme von **Server**. Der Treiber Msorcl32.dll (Version 2.0 und höher) unterstützt alle Einstellungen.  
  
 Einige Einstellungen werden vom Treiber ignoriert jedoch akzeptiert werden, indem **SQLConfigDatasource**. Z. B. diese Einstellungen in der ODBC-Verbindungszeichenfolge ist die einzige Möglichkeit, die sie zur Laufzeit akzeptiert werden. Eine ignorierte-Einstellung wird nicht gespeichert werden, in der Registrierung beim **SQLConfigDatasource** erstellt die Datenquelle.  
  
 In der folgenden Tabelle *eine/N* bedeutet, dass eine beliebige gültige alphanumerische Zeichenfolge bis zu die maximal zulässige Länge. *Max. Len* (maximale Länge) ist die maximale zulässige Zeichenfolgenlänge von der Einstellung, einschließlich des Zeichens der Zeichenfolge-Terminator akzeptiert.  
  
|Einstellung|Max. Länge|Standardwert|Gültige Werte|Beschreibung|  
|-------------|-------------|-------------------|------------------|-----------------|  
|Puffergröße|7|65535|1000|Minimale Fetchpuffer Größe bis 65535 Bytes.|  
|CatalogCap|2|1|0 oder 1|Bei 1 werden nonquoted Bezeichner in Großbuchstaben umwandeln, in dem Katalog Funktionen.|  
|ConnectString|128|""|A/N|Verbindungszeichenfolge. Erforderliche Methode den Namen des Servers mit dem Treiber Msorcl10.dll angeben.|  
|Beschreibung|256|""|A/N|Beschreibung|  
|DSN|33|""|A/N|Datenquellenname.|  
|GuessTheColDef|4|0|A/N|Gibt einen Wert ungleich NULL für Spalten ohne Skalierbarkeit Oracle definiert.|  
|NumberFloat|2|""|0 oder 1|Wenn der Wert 0 ist, werden FLOAT-Spalten als SQL_FLOAT behandelt. Bei 1 werden FLOAT-Spalten als SQL_DOUBLE behandelt.|  
|PWD|30|""|A/N|Das Kennwort.|  
|RDOSupport|2|""|0 oder 1|Ermöglicht das RDO Oracle Prozeduren aufrufen.|  
|Hinweise|2|0|0 oder 1|Schließen Sie "Hinweise" in Katalogfunktionen an.|  
|RowLimit|4|""|0 bis 99|Maximale Anzahl der von einer SELECT-Anweisung zurückgegebenen Zeilen. Eine Zeichenfolge der Länge 0 (null) gibt an, dass keine Beschränkung angewendet wird.|  
|Server|128|""|A/N|Der Name der Oracle-Servers.|  
|SynonymColumns|2|1|0 oder 1|Synonyme in SQLColumns einschließen.|  
|SystemTable|2|""|0 oder 1|Bei 0 werden die Systemtabellen nicht angezeigt. Bei 1 werden den Systemtabellen angezeigt.|  
|TranslationDLL|33|""|A/N|Translation-DLL-Namen.|  
|TranslationName|33|""|A/N|Name der Übersetzung.|  
|TranslationOption|33|""|A/N|Translation-Option.|  
|TxnCap|2|""|A/N|Die Transaktion kann. Bei 0, gibt der Treiber, dass es keine Transaktionen unterstützt. Falls 1, gibt der Treiber, dass sie Transaktionen ausführen kann.|  
|UID|30|""|A/N|Name des Benutzers.|
