---
title: Definieren des Textformats (Textdateitreiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 500a81146397fa5c50bd8b74c600d04887ecc99c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096354"
---
# <a name="defining-text-format-text-file-driver"></a>Definieren des Textformats (Textdateitreiber)
Wenn der Text-Treiber verwendet wird, können Sie die **-Text-Format definieren** Dialogfeld, um das Format für Spalten in einer ausgewählten Datei zu definieren. Dieses Dialogfeld können Sie das Schema für jede Datentabelle anzugeben. Diese Informationen werden in eine Schema.ini-Datei im Data Source-Verzeichnis geschrieben. Eine separate Datei Schema.ini wird für jeden Text Data Source-Verzeichnis erstellt.  
  
> [!NOTE]  
>  Das gleiche Standarddateiformat gilt für alle neuen Datentabellen von Text. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt, erben die gleichen Format Standardwerte, die festgelegt werden, durch Auswählen von Format dateiwerten in die **-Text-Format definieren** Dialogfeld mit \<standardmäßig > in der ausgewählten**Tabellen** Liste. Der Treiber Text ändert sich nicht auf das Format einer vorhandenen Textdatei entsprechend das in diesem Dialogfeld definierte Format, aber es gibt einen Fehler zurück, wenn das Format, z. B., wenn versucht wird, Abrufen von Daten aus der Textdatei verwendet.  
  
 Die folgenden Optionen stehen in der **-Text-Format definieren** Dialogfeld:  
  
|Option|Information|  
|------------|-----------------|  
|**Hinzufügen**|Fügt eine Spalte mit den Werten in **Datentyp**, **Namen**, und **Breite** aus dem Dialogfeld, und falls zutreffend, Datumstrennzeichen Schema.ini Wert.|  
|**Zeichen**|**ANSI** oder **OEM**. OEM-Abhängige gibt einen nicht-ANSI-Zeichensatz an. Wenn das Format des Elements in ausgewählt. für OEM standardmäßig die **Tabellen** Liste wurde durch dieses Dialogfeld können Sie nicht zuvor definiert.|  
|**Kopfzeile der Spalte Name**|Gibt an, ob die Spalten der ausgewählten Tabelle die erste Zeile als Spaltennamen verwendet werden soll. Entweder **"true"** oder **"false"** . Standardmäßig auf "false" fest, wenn das Format des ausgewählten Elements in der **Tabellen** Liste wurde durch dieses Dialogfeld können Sie nicht zuvor definiert.|  
|**Spalten**|Listet die Spaltennamen für jede Spalte in der ausgewählten Tabelle. Die Reihenfolge der Spalten gibt die Reihenfolge der Spalten in der Tabelle wieder. Diese Liste ist aktiviert, wenn eine Datei ausgewählt wurde die **Tabellen** Liste.|  
|**Datentyp**|BIT, BYTE, CHAR, Währung, Datum, "float", ganze Zahl, LONGCHAR, SHORT oder einzelne möglich. Date-Datentypen können in den folgenden Formaten werden: "tt-mmm-Yy", "mm-Dd-Yy", "mmm-JJ", "Yyyy-mm-Dd" oder "Yyyy-mmm-Dd". "mm" gibt die Zahlen für Monate; "mmm" gibt die Buchstaben für Monate an.|  
|**Trennzeichen**|Gibt an, das benutzerdefinierte Trennzeichen zum Trennen der Spalten verwendet werden. Aktiviert, wenn die **benutzerdefinierte Trennzeichen** Format ausgewählt ist. Das Trennzeichen kann nur ein Zeichen lang sein, und doppelte Anführungszeichen (") kann nicht als Trennzeichen verwendet werden. (Das Trennzeichen kann nicht im Hexadezimal-oder Dezimalformat angegeben werden.)|  
|**Format**|Mit Trennzeichen oder mit fester Länge. Wenn Trennzeichen, gibt Sie den Typ der verwendeten Trennzeichen: durch Kommas (CSV), Tabstopp oder Sonderzeichen (Benutzerdefiniert). Der Standardwert lautet **CSV-Trennzeichen** , wenn das Format des Elements in ausgewählt der **Tabellen** Liste wurde durch dieses Dialogfeld können Sie nicht zuvor definiert.<br /><br /> Wenn **Format** fester Länge ist und **Kopfzeile der Spalte Name** ist "true", die erste Zeile muss durch Kommas getrennt sein.|  
|**Schätzung**|Generiert automatisch die Werte der Spalte Daten Typ, Name und die Breite der Spalten in der ausgewählten Tabelle durch das Scannen des Tabelleninhalts gemäß der **Format** Feld-Auswahl. Aktiviert, wenn das Tabellenformat getrennt wird. Alle zuvor definierten Spalten in der **Spalten** Liste gelöscht und mit neuen Einträgen ersetzt werden. Wenn **Kopfzeile der Spalte Name** ist nicht ausgewählt ist, Spaltennamen automatisch generiert werden als "F1", "F2" und So weiter. Kein Standardwert wird angezeigt, der **Datentyp** Feld.<br /><br /> Diese Funktion kann nur für Spalten, die kleiner ist als 64,513 Bytes sind.|  
|**Ändern**|Ändert die ausgewählte Spalte, die mithilfe der Werte in **Datentyp**, **Namen**, und **Breite**.|  
|**Name**|Zeigt den Namen der ausgewählten Spalte an. Kann verwendet werden, um einen neuen Spaltennamen für eine vorhandene Spalte oder eine neue Spalte anzugeben.<br /><br /> Wenn **Kopfzeile der Spalte Name** ist "true", der Spalte angezeigte Name wird ignoriert.|  
|**Entfernen**|Löscht die ausgewählte Spalte an.|  
|**Zu scannende Zeilen**|Die Anzahl der Zeilen, die von Setup oder der Treiber überprüft werden, wenn Sie die Spalten und Spaltendatentypen basierend auf den vorhandenen Daten festlegen.<br /><br /> Sie können eine Zahl zwischen 1 und 32767 für die Anzahl der zu durchsuchenden Zeilen eingeben. Dies ist standardmäßig auf 25, wenn das Format des ausgewählten Elements in der **Tabellen** Liste wurde durch dieses Dialogfeld können Sie nicht zuvor definiert. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)|  
|**Tabellen**|Enthält eine Liste aller Dateien in das Verzeichnis, die im ausgewählten der **Text Setup** (Dialogfeld), die mit die Liste der angegebenen Erweiterungen übereinstimmen.<br /><br /> Wenn \<standardmäßig > ausgewählt ist, und eine der folgenden ist "true" werden die Werte von Attributen in den Tabellen in der **Tabellen** Gruppe in "Schema.ini" (es sind keine weiteren Einträge in "Schema.ini" verwendete) geschrieben werden:<br /><br /> – Es gibt keine Schema.ini im angegebenen Verzeichnis.<br />-Die Schema.ini-Datei vorhanden ist, aber es gibt keine in Schema.ini eines Text-Dateien (mit der angegebenen Erweiterung) im Verzeichnis.<br />-Abschnitt für eine Textdatei, die in "Schema.ini" vorhanden ist, aber der Nachrichtentext leer ist.<br /><br /> Wenn \<standardmäßig > aktiviert ist, die **Spalten** -Gruppe deaktiviert ist.|  
|**Width**|Die Breite der Spalte kann für CHAR "oder" LONGCHAR Spalten geändert werden. Die Breite wird standardmäßig auf 1 fest, wenn das Format des ausgewählten Elements in der **Tabellen** Liste wurde durch dieses Dialogfeld können Sie nicht zuvor definiert.<br /><br /> Klicken Sie für andere Datentypen Steuerung der Breite ist deaktiviert, und wird kein Wert angezeigt.|
