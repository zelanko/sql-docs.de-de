---
title: Definieren des Textformats (Textdateitreiber) | Microsoft Docs
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
ms.openlocfilehash: 29dc46525f3c81e5abffe5076988716a01df06df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307661"
---
# <a name="defining-text-format-text-file-driver"></a>Definieren des Textformats (Textdateitreiber)
Wenn der Texttreiber verwendet wird, können Sie das Dialogfeld **Textformat definieren** verwenden, um das Format für Spalten in einer ausgewählten Datei zu definieren. In diesem Dialogfeld können Sie das Schema für jede Datentabelle angeben. Diese Informationen werden in eine Schema.ini-Datei im Datenquellenverzeichnis geschrieben. Für jedes Textdatenquellenverzeichnis wird eine separate Datei Schema.ini erstellt.  
  
> [!NOTE]  
>  Das gleiche Standarddateiformat gilt für alle neuen Textdatentabellen. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt werden, erben dieselben Standardformatwerte, die \<durch Auswählen von Dateiformatwerten im Dialogfeld **Textformat** definieren mit standardmäßigen> in der Liste **Tabellen** ausgewählt werden. Der Texttreiber ändert das Format einer vorhandenen Textdatei nicht so, dass es dem in diesem Dialogfeld definierten Format entspricht, gibt jedoch einen Fehler zurück, wenn er das Format verwendet, z. B. wenn versucht wird, Daten aus der Textdatei abzurufen.  
  
 Die folgenden Optionen sind im Dialogfeld **Textformat** definieren verfügbar:  
  
|Option|Information|  
|------------|-----------------|  
|**Hinzufügen**|Fügt eine Spalte mit den Werten in **Datentyp**, **Name**und **Breite** aus dem Dialogfeld und ggf. den Datumstrennwert von Schema.ini hinzu.|  
|**Zeichen**|**ANSI** oder **OEM**. OEM gibt einen Nicht-ANSI-Zeichensatz an. Dies ist standardmäßig OEM, wenn das Format des in **der** Tabellenliste ausgewählten Elements in diesem Dialogfeld nicht zuvor definiert wurde.|  
|**Spaltenname-Header**|Gibt an, ob die Spalten der ersten Zeile der ausgewählten Tabelle als Spaltennamen verwendet werden sollen. Entweder **TRUE** oder **FALSE**. Standardeinstellung als FALSE, wenn das Format des in **der** Tabellenliste ausgewählten Elements in diesem Dialogfeld nicht zuvor definiert wurde.|  
|**Spalten**|Listet die Spaltennamen für jede Spalte in der ausgewählten Tabelle auf. Die Reihenfolge der Spalten gibt die Reihenfolge der Spalten in der Tabelle an. Diese Liste ist aktiviert, wenn eine Datei in der Liste **Tabellen** ausgewählt wurde.|  
|**Datentyp**|Kann BIT, BYTE, CHAR, CURRENCY, DATE, FLOAT, INTEGER, LONGCHAR, SHORT oder SINGLE sein. Datumsdatentypen können in den folgenden Formaten vorliegen: "dd-mmm-yy", "mm-dd-yy", "mmm-dd-yy", "yyyy-mm-dd" oder "yyyy-mmm-dd". "mm" bezeichnet Zahlen für Monate; "mmm" bezeichnet Briefe für Monate.|  
|**Trennzeichen**|Gibt das benutzerdefinierte Trennzeichen an, das zum Trennen von Spalten verwendet werden soll. Aktiviert, wenn das **Format benutzerdefinierte Trennzeichen** ausgewählt ist. Das Trennzeichen kann nur ein Zeichen lang sein, und doppelte Anführungszeichen (") können nicht als Trennzeichen verwendet werden. (Das Trennzeichen kann nicht im hexadezimalen oder dezimalen Format angegeben werden.)|  
|**Format**|Entweder abgegrenzt oder feste Länge. Wenn diese Trennzeichen getrennt sind, gibt der Typ des verwendeten Trennzeichens an: Komma (CSV), Registerkarte oder Sonderzeichen (custom). Dies ist standardmäßig **CSV-Trennzeichen,** wenn das Format des in **der** Tabellenliste ausgewählten Elements in diesem Dialogfeld nicht zuvor definiert wurde.<br /><br /> Wenn **Format** eine feste Länge ist und **Der Spaltennamenkopf** TRUE ist, muss die erste Zeile durch Kommas getrennt sein.|  
|**schätze**|Generiert automatisch die Datentyp-, Namens- und Breitenwerte der Spalte für die Spalten in der ausgewählten Tabelle, indem der Inhalt der Tabelle gemäß der Feldauswahl **Format** gescannt wird. Aktiviert, wenn das Tabellenformat durch Trennzeichen getrennt ist. Alle zuvor definierten Spalten in **der** Spaltenliste werden gelöscht und durch neue Einträge ersetzt. Wenn **der Spaltennamen-Header** nicht ausgewählt ist, werden Spaltennamen automatisch als "F1", "F2" usw. generiert. Im Feld **Datentyp** wird kein Standardwert angezeigt.<br /><br /> Diese Funktionalität funktioniert nur für Spalten, die weniger als 64.513 Bytes haben.|  
|**Modify**|Ändert die ausgewählte Spalte mithilfe der Werte in **Datentyp**, **Name**und **Breite**.|  
|**Name**|Zeigt den Namen der ausgewählten Spalte an. Kann verwendet werden, um einen neuen Spaltennamen für eine vorhandene Spalte oder eine neue Spalte anzugeben.<br /><br /> Wenn **Column Name Header** TRUE ist, wird der angezeigte Spaltenname ignoriert.|  
|**Entfernen**|Löscht die ausgewählte Spalte.|  
|**Zeilen zum Scannen**|Die Anzahl der Zeilen, die Setup oder der Treiber scannen, wenn die Spalten und Spaltendatentypen basierend auf vorhandenen Daten gesetzt werden.<br /><br /> Sie können eine Zahl von 1 bis 32767 für die Anzahl der zu scannenden Zeilen eingeben. Dies entspricht der Standardeinstellung 25, wenn das Format des in **der** Tabellenliste ausgewählten Elements in diesem Dialogfeld nicht zuvor definiert wurde. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|  
|**Tabellen**|Enthält eine Liste aller Dateien im Verzeichnis, die im Dialogfeld **Texteinrichtung** ausgewählt sind und mit der Liste der angegebenen Erweiterungen übereinstimmen.<br /><br /> Wenn \<die> standardmäßig ausgewählt ist und einer der folgenden Werte wahr ist, werden die Werte der Tabellenattribute in der Gruppe **Tabellen** in Schema.ini geschrieben (keine anderen Einträge in Schema.ini werden berührt):<br /><br /> - Das angegebene Verzeichnis enthält kein Schema.ini.<br />- Die Datei Schema.ini ist vorhanden, aber es gibt keinen Abschnitt in Schema.ini für eine der Textdateien (mit der angegebenen Erweiterung) im Verzeichnis.<br />- Der Abschnitt für eine Textdatei ist in Schema.ini vorhanden, aber der Textkörper ist leer.<br /><br /> Wenn \<die Standard> ausgewählt ist, ist die Gruppe **Spalten** deaktiviert.|  
|**Width**|Die Breite der Spalte kann für CHAR- oder LONGCHAR-Spalten geändert werden. Die Breite ist standardmäßig 1, wenn das Format des in **der** Tabellenliste ausgewählten Elements in diesem Dialogfeld nicht zuvor definiert wurde.<br /><br /> Bei anderen Datentypen ist das Breitensteuerelement deaktiviert, und es wird kein Wert angezeigt.|
