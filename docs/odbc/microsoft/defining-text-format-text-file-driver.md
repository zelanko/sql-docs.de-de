---
description: Definieren des Textformats (Textdateitreiber)
title: Definieren des Text Formats (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: 3af46dad-52cc-4d5c-a27e-6315d65a74e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe992d4ea7cf81387bc56ef9c384404b015b52a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340946"
---
# <a name="defining-text-format-text-file-driver"></a>Definieren des Textformats (Textdateitreiber)
Wenn der Text Treiber verwendet wird, können Sie das Dialogfeld **Text Format definieren** verwenden, um das Format für Spalten in einer ausgewählten Datei zu definieren. In diesem Dialogfeld können Sie das Schema für jede Datentabelle angeben. Diese Informationen werden in eine Schema.ini Datei im Datenquellen Verzeichnis geschrieben. Eine separate Schema.ini Datei wird für jedes Text Datenquellen Verzeichnis erstellt.  
  
> [!NOTE]  
>  Das gleiche Standarddatei Format gilt für alle neuen Text Datentabellen. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt werden, erben dieselben Standardformat Werte. Diese werden festgelegt, indem die Dateiformat Werte im Dialogfeld **Text Format definieren** \<default> ausgewählt und in der Liste **Tabellen** ausgewählt werden. Der Text Treiber ändert nicht das Format einer vorhandenen Textdatei, sodass Sie dem in diesem Dialogfeld definierten Format entspricht, gibt jedoch einen Fehler zurück, wenn das Format verwendet wird, z. b. wenn versucht wird, Daten aus der Textdatei abzurufen.  
  
 Die folgenden Optionen sind im Dialogfeld **Text Format definieren** verfügbar:  
  
|Option|Information|  
|------------|-----------------|  
|**Add (Hinzufügen)**|Fügt eine Spalte mithilfe der Werte in **Datentyp**, **Name**und **Breite** aus dem Dialogfeld und ggf. dem Datums Trennzeichen Wert aus Schema.ini hinzu.|  
|**Zeichen**|**ANSI** oder **OEM**. OEM gibt einen nicht-ANSI-Zeichensatz an. Standardmäßig wird OEM verwendet, wenn das Format des in der Liste **Tabellen** ausgewählten Elements nicht zuvor in diesem Dialogfeld definiert wurde.|  
|**Spaltennamen Header**|Gibt an, ob die Spalten der ersten Zeile der ausgewählten Tabelle als Spaltennamen verwendet werden sollen. Entweder **true** oder **false**. Der Standardwert ist false, wenn das Format des Elements, das in der **Tabellen** Liste ausgewählt wurde, nicht zuvor in diesem Dialogfeld definiert wurde.|  
|**Spalten**|Listet die Spaltennamen für jede Spalte in der ausgewählten Tabelle auf. Die Reihenfolge der Spalten zeigt die Reihenfolge der Spalten in der Tabelle an. Diese Liste ist aktiviert, wenn eine Datei in der Liste **Tabellen** ausgewählt wurde.|  
|**Datentyp**|Kann Bit, Byte, Char, Currency, Date, float, Integer, LONGCHAR, Short oder Single sein. Datums Datentypen können die folgenden Formate aufweisen: "dd-mmm-yy", "mm-dd-yy", "MMM-dd-yy", "yyyy-mm-dd" oder "yyyy-MMM-DD". "mm" bezeichnet Zahlen für Monate. "MMM" bezeichnet Buchstaben für Monate.|  
|**Trennzeichen**|Gibt das benutzerdefinierte Trennzeichen an, das zum Trennen von Spalten verwendet werden soll. Aktiviert, wenn das **benutzerdefinierte** , durch Trennzeichen getrennte Format ausgewählt ist. Das Trennzeichen darf nur ein Zeichen lang sein, und doppelte Anführungszeichen (") können nicht als Trennzeichen verwendet werden. (Das Trennzeichen kann nicht im Hexadezimal-oder Dezimal Format angegeben werden.)|  
|**Format**|Entweder mit Trennzeichen oder mit fester Länge. Wenn Sie getrennt ist, wird der Typ des verwendeten Trenn Zeichens angegeben: Komma (CSV), Tabulator oder Sonderzeichen (Benutzer definiert). Standardmäßig wird ein **CSV-Trenn** Zeichen verwendet, wenn das in der Liste **Tabellen** ausgewählte Element nicht zuvor in diesem Dialogfeld definiert wurde.<br /><br /> Wenn **Format** eine Länge mit fester Länge und der **Spaltennamen Header** true ist, muss die erste Zeile durch Kommas getrennt werden.|  
|**Vermute**|Generiert automatisch den Datentyp, den Namen und die Breitenwerte der Spalte für die Spalten in der ausgewählten Tabelle, indem der Inhalt der Tabelle gemäß der **Format** Feldauswahl überprüft wird. Aktiviert, wenn das Tabellenformat als Trennzeichen verwendet wird. Alle zuvor definierten Spalten in der **Spalten** Liste werden gelöscht und durch neue Einträge ersetzt. Wenn die **Spaltennamen Kopfzeile** nicht ausgewählt ist, werden Spaltennamen automatisch als "F1", "F2" usw. generiert. Im Feld **Datentyp** wird kein Standardwert angezeigt.<br /><br /> Diese Funktion funktioniert nur bei Spalten, die kleiner als 64.513 Bytes sind.|  
|**Modify** (Ändern)|Ändert die ausgewählte Spalte mit den Werten in **Datentyp**, **Name**und **Breite**.|  
|**Name**|Zeigt den Namen der ausgewählten Spalte an. Kann verwendet werden, um einen neuen Spaltennamen für eine vorhandene Spalte oder eine neue Spalte anzugeben.<br /><br /> Wenn der **Spaltennamen Header** true ist, wird der angezeigte Spaltenname ignoriert.|  
|**Remove**|Löscht die ausgewählte Spalte.|  
|**Zu überprüfenden Zeilen**|Die Anzahl der Zeilen, die von Setup oder Treiber beim Festlegen der Spalten-und Spaltendatentypen basierend auf den vorhandenen Daten überprüft werden.<br /><br /> Sie können eine Zahl zwischen 1 und 32767 für die Anzahl der zu überprüfenden Zeilen eingeben. Der Standardwert ist 25, wenn das in der Liste **Tabellen** ausgewählte Element nicht zuvor von diesem Dialogfeld definiert wurde. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|  
|**Tabellen**|Enthält eine Liste aller Dateien in dem Verzeichnis, das im Dialogfeld **Text Setup** ausgewählt ist, das der Liste der angegebenen Erweiterungen entspricht.<br /><br /> Wenn \<default> ausgewählt ist und eine der folgenden Werte zutrifft, werden die Werte der Tabellen Attribute in der Gruppe **Tabellen** in Schema.ini geschrieben (keine weiteren Einträge in Schema.ini sind berührt):<br /><br /> -Es ist keine Schema.ini im angegebenen Verzeichnis vorhanden.<br />-Die Schema.ini Datei ist vorhanden, aber es gibt keinen Abschnitt in Schema.ini für eine der Text Dateien (mit der angegebenen Erweiterung) im Verzeichnis.<br />-Der Abschnitt für eine Textdatei ist in Schema.ini vorhanden, aber der Text ist leer.<br /><br /> Wenn \<default> ausgewählt ist, wird die Gruppe **Spalten** deaktiviert.|  
|**Width**|Die Breite der Spalte kann für char-oder LONGCHAR-Spalten geändert werden. Die Breite ist standardmäßig auf 1 festgelegt, wenn das in der Liste **Tabellen** ausgewählte Element nicht zuvor in diesem Dialogfeld definiert wurde.<br /><br /> Bei anderen Datentypen ist das width-Steuerelement deaktiviert, und es wird kein Wert angezeigt.|
