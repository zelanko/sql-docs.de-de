---
title: Hinzufügen und Ändern von Datenquellen mithilfe von Setup | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], adding
- editing data sources [ODBC], ODBC driver for Oracle
- adding data sources [ODBC], ODBC driver for Oracle
- data sources [ODBC], changing
- data sources [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], adding data sources
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae76abc902e4687e5d9891871d7d5d60598b3abc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281410"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Erstellen und Ändern von Datenquellen mithilfe der Einrichtung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Eine Datenquelle identifiziert einen Pfad zu Daten, der eine Netzwerkbibliothek, einen Server, eine Datenbank und andere Attribute enthalten kann – in diesem Fall ist die Datenquelle der Pfad zu einer Oracle-Datenbank. Um eine Verbindung mit einer Datenquelle herzustellen, überprüft der Treiber-Manager die Windows-Registrierung auf bestimmte Verbindungsinformationen.  
  
 Der vom ODBC-Datenquellenadministrator erstellte Registrierungseintrag wird von den ODBC-Treibern "Treiber" und "ODBC" verwendet. Dieser Eintrag enthält Informationen zu jeder Datenquelle und dem zugehörigen Treiber. Bevor Sie eine Verbindung mit einer Datenquelle herstellen können, müssen deren Verbindungsinformationen der Registrierung hinzugefügt werden.  
  
 Um Datenquellen hinzuzufügen und zu konfigurieren, verwenden Sie den [ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md). Der ODBC-Administrator aktualisiert Ihre Datenquellenverbindungsinformationen. Beim Hinzufügen von Datenquellen aktualisiert der ODBC-Administrator die Registrierungsinformationen für Sie.  
  
### <a name="to-add-a-data-source-for-windows"></a>So fügen Sie eine Datenquelle für Windows hinzu  
  
1.  Öffnen Sie den ODBC-Datenquellenadministrator.  
  
2.  Klicken Sie im Dialogfeld ODBC Data Source Administrator auf Hinzufügen. Das Dialogfeld Creat New Data Source wird angezeigt.  
  
3.  Wählen Sie Microsoft ODBC für Oracle aus, und klicken Sie dann auf Fertig stellen. Das Dialogfeld Microsoft ODBC für Oracle Setup wird angezeigt.  
  
4.  Geben Sie im Feld Datenquellenname den Namen der Datenquelle ein, auf die Sie zugreifen möchten. Es kann sich um jeden Namen handelt, den Sie wählen.  
  
5.  Geben Sie im Feld Beschreibung die Beschreibung für den Treiber ein. Dieses optionale Feld beschreibt den Datenbanktreiber, mit dem die Datenquelle eine Verbindung herstellt. Es kann sich um jeden Namen handelt, den Sie wählen.  
  
6.  Geben Sie im Feld Benutzername den Datenbankbenutzernamen (Ihre Datenbankbenutzer-ID) ein.  
  
7.  Geben Sie im Feld Server den Datenbankalias ein, oder verbinden Sie die Zeichenfolge für das Oracle Server-Modul, auf das Sie zugreifen möchten.  
  
8.  Klicken Sie auf OK, um diese Datenquelle hinzuzufügen.  
  
> [!NOTE]  
>  Das Dialogfeld Datenquellen wird angezeigt, und der ODBC-Administrator aktualisiert die Registrierungsinformationen. Der eingegebene Benutzername und die Verbindungszeichenfolge werden zum Standardverbindungswert für diese Datenquelle, wenn Sie eine Verbindung herstellen.  
  
1.  Klicken Sie auf Optionen, um weitere Spezifikationen zum ODBC-Treiber für Oracle-Setup zu machen:  
  
    -   **Übersetzung** – Klicken Sie auf Auswählen, um einen geladenen Datenübersetzer auszuwählen. Der Standardwert ist \<No Translator>.  
  
    -   **Leistung** – Das Kontrollkästchen REMARKS in Katalogfunktionen einschließen gibt an, ob der Treiber Anmerkungsspalten für das [SQLColumns-Resultset](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) zurückgibt. Der ODBC-Treiber für Oracle bietet einen schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.  
  
         Das Kontrollkästchen SYNONYMS in SQL-Spalten einschließen gibt an, ob der Treiber Spalteninformationen zurückgibt. **Puffergröße** gibt die Größe in Bytes an, die dem Empfang abgerufener Daten zugewiesen ist. Der Treiber optimiert das Abrufen, sodass ein Abruf vom Oracle Server genügend Zeilen zurückgibt, um einen Puffer der angegebenen Größe zu füllen. Größere Werte erhöhen tendenziell die Leistung beim Abrufen vieler Daten.  
  
    -   **Anpassung** - Das Kontrollkästchen "ENFORCE ODBC DayOfWeek Standard" gibt an, ob das Resultset dem von ODBC angegebenen Tag-of-Week-Format entspricht (Sonntag = 1; Samstag = 7). Wenn dieses Kontrollkästchen deaktiviert ist, wird der gebietsschemaspezifische Oracle-Wert zurückgegeben.  
  
         Das Kontrollkästchen SQLDescribeCol **gibt immer einen Wert für** das Genauigkeits-Kontrollkästchen an, ob der Treiber einen Wert ungleich Null für das *cbColDef-Argument* von **SQLDescribeCol**zurückgeben soll. Dieses Verbindungszeichenfolgenattribut gilt nur für Spalten, in denen es keinen Oracle-definierten Maßstab gibt, z. B. berechnete numerische Spalten und Spalten, die als NUMBER ohne Genauigkeit oder Skalierung definiert sind. Ein **SQLDescribeCol-Aufruf** gibt 130 für die Genauigkeit zurück, wenn Oracle diese Informationen nicht zur Verfügung stellt. Wenn dieses Kontrollkästchen deaktiviert ist, gibt der Treiber stattdessen 0 für diese Spaltentypen zurück.  
  
2.  Klicken Sie auf Hinzufügen, um eine weitere Datenquelle hinzuzufügen, oder klicken Sie auf Schließen, um den Vorgang zu beenden.  
  
### <a name="to-modify-a-data-source-for-windows"></a>So ändern Sie eine Datenquelle für Windows  
  
1.  Öffnen Sie den ODBC-Datenquellenadministrator. Klicken Sie auf die entsprechende Registerkarte DSN.  
  
2.  Wählen Sie die Oracle-Datenquelle aus, die Sie ändern möchten, und klicken Sie dann auf Konfigurieren. Das Dialogfeld Microsoft ODBC für Oracle Setup wird angezeigt.  
  
3.  Ändern Sie die entsprechenden Datenquellenfelder, und klicken Sie dann auf OK.  
  
 Wenn Sie die Änderung der Informationen in diesem Dialogfeld abgeschlossen haben, aktualisiert der ODBC-Administrator die Registrierungsinformationen.
