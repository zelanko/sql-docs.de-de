---
title: Verwenden von SQLConfigDataSource mit dem ODBC-Treiber für Oracle | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292770"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Verwenden von SQLConfigDatasource mit dem ODBC-Treiber für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In der folgenden Tabelle sind die gültigen **SQLConfigDataSource** -Einstellungen für den Microsoft ODBC Driver for Oracle, Version 1,0 (Msorcl10. dll) und der Microsoft ODBC Driver for Oracle, Version 2,0 (Msorcl32. dll), aufgeführt.  
  
> [!NOTE]  
>  Der Msorcl10. dll-Treiber (Version 1,0) unterstützt alle Einstellungen außer " **Server**". Der Msorcl32. dll-Treiber (Version 2,0 und höher) unterstützt alle Einstellungen.  
  
 Einige Einstellungen werden vom Treiber ignoriert, aber von **SQLConfigDataSource**akzeptiert. Das einschließen dieser Einstellungen in die ODBC-Verbindungs Zeichenfolge ist die einzige Möglichkeit, Sie zur Laufzeit zu akzeptieren. Eine ignorierte Einstellung wird nicht in der Registrierung gespeichert, wenn **SQLConfigDataSource** die Datenquelle erstellt.  
  
 In der folgenden Tabelle bedeutet *A/N eine* beliebige gültige alphanumerische Zeichenfolge bis zur maximalen zulässigen Länge. *Max len* (maximale Länge) ist die maximal zulässige Zeichen folgen Länge, die von der Einstellung akzeptiert wird, einschließlich des Zeichen folgen Abschluss Zeichens.  
  
|Einstellung|Max. Len|Standardwert|Gültige Werte|BESCHREIBUNG|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65.535|1000|Minimale Abruf Puffergröße bis zu 65535 Bytes|  
|Catalogcap|2|1|0 oder 1|Wenn 1, werden Bezeichner ohne Anführungszeichen in den Katalog Funktionen in Großbuchstaben konvertiert.|  
|ConnectString|128|""|A/N|Verbindungszeichenfolge. Erforderliche Methode zum Angeben des Server namens mit dem Msorcl10. dll-Treiber.|  
|BESCHREIBUNG|256|""|A/N|Beschreibung|  
|DSN|33|""|A/N|Der Name der Datenquelle.|  
|Guess thecoldef|4|0|A/N|Gibt einen Wert ungleich 0 (null) für Spalten ohne Oracle-definierte Skala zurück.|  
|Nummerifloat|2|""|0 oder 1|Wenn der Wert 0 ist, werden float-Spalten als SQL_FLOAT behandelt. Wenn der Wert 1 ist, werden float-Spalten als SQL_DOUBLE behandelt.|  
|PWD|30|""|A/N|Password:|  
|Rdosupport|2|""|0 oder 1|Ermöglicht RDO das Abrufen von Oracle-Prozeduren.|  
|Bemerkungen|2|0|0 oder 1|Fügen Sie Hinweise in Katalog Funktionen ein.|  
|ROWLIMIT|4|""|0 bis 99|Maximale Anzahl von Zeilen, die von einer SELECT-Anweisung zurückgegeben werden. Eine Zeichenfolge der Länge 0 (null) gibt an, dass keine Beschränkung angewendet wird.|  
|Server|128|""|A/N|Der Name des Oracle-Servers.|  
|Synonymcolumns|2|1|0 oder 1|Fügen Sie Synonyme in SQLColumns ein.|  
|SystemTable|2|""|0 oder 1|Wenn der Wert 0 ist, werden die Systemtabellen nicht angezeigt. Bei 1 werden Systemtabellen angezeigt.|  
|TranslationDLL|33|""|A/N|Der Name der Translation. dll.|  
|TranslationName|33|""|A/N|Der Übersetzungs Name.|  
|"TranslationOption"|33|""|A/N|Übersetzungs Option.|  
|Txncap|2|""|A/N|Transaktionsfähig. Wenn der Wert 0 ist, meldet der Treiber, dass Transaktionen nicht unterstützt werden. Wenn der Wert 1 ist, meldet der Treiber, dass er Transaktionen ausführen kann.|  
|UID|30|""|A/N|Benutzername.|
