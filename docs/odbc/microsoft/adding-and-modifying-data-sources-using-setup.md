---
title: Hinzufügen und Ändern von Datenquellen mithilfe des Setups | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953563285d3c62a8523079a604cf607f2e0edf62
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63219110"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Erstellen und Ändern von Datenquellen mithilfe der Einrichtung
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Eine Datenquelle gibt einen Pfad zu den Daten, die eine Netzwerkbibliothek, Server, Datenbank und andere Attribute enthalten können: in diesem Fall die Datenquelle ist der Pfad zu einer Oracle-Datenbank. Um eine Verbindung mit einer Datenquelle herzustellen, überprüft der Treiber-Manager die Windows-Registrierung für Verbindungsinformationen an.  
  
 Der Registrierungseintrag, der von ODBC-Datenquellen-Administrator erstellt, wird von der ODBC-Treiber-Manager und ODBC-Treiber verwendet. Dieser Eintrag enthält Informationen über jede Datenquelle und den zugehörigen Treiber. Bevor Sie mit einer Datenquelle verbinden können, muss die Verbindungsinformationen in der Registrierung hinzugefügt werden.  
  
 Verwenden Sie zum Hinzufügen und Konfigurieren von Datenquellen, die [ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md). Der ODBC-Administrator aktualisiert Ihre Datenquellen-Verbindungsinformationen an. Hinzufügen von Datenquellen aktualisiert den ODBC-Administrator die Informationen in der Registrierung für Sie.  
  
### <a name="to-add-a-data-source-for-windows"></a>Hinzufügen eine Datenquelle für Windows  
  
1.  Öffnen Sie die ODBC-Datenquellen-Administrator.  
  
2.  Klicken Sie auf "hinzufügen", klicken Sie im Dialogfeld ODBC-Datenquellen-Administrator. Das Dialogfeld "neue Datenquelle erstellen" angezeigt wird.  
  
3.  Wählen Sie Microsoft ODBC für Oracle, und klicken Sie dann auf "Fertig stellen". Microsoft ODBC für Oracle-Setup-Dialogfeld wird angezeigt.  
  
4.  Geben Sie im Data Source Name den Namen der Datenquelle, die Sie zugreifen möchten. Es kann ein beliebiger Name sein, die Sie auswählen.  
  
5.  Geben Sie im Feld Beschreibung die Beschreibung für den Treiber aus. Dieses optionale Feld beschreibt den ODBC-Treiber, dem mit die Datenquelle verbindet. Es kann ein beliebiger Name sein, die Sie auswählen.  
  
6.  Geben Sie im Feld Benutzername Ihrer Datenbank-Benutzernamen (die Datenbankbenutzer-ID).  
  
7.  Geben Sie in das Feld den Alias der Datenbank, oder die Verbindungszeichenfolge für die Oracle-Server-Engine, die Sie zugreifen möchten.  
  
8.  Klicken Sie auf OK, um diese Datenquelle hinzuzufügen.  
  
> [!NOTE]  
>  Das Dialogfeld "Datenquellen" angezeigt wird, und den ODBC-Administrator aktualisiert die Informationen in der Registrierung. Der Benutzer benennen und die Verbindungszeichenfolge, die von Ihnen eingegebene werden die Standardwerte für die Verbindung für diese Datenquelle aus, wenn Sie eine Verbindung damit herstellen.  
  
1.  Klicken Sie auf Optionen stellen weitere Angaben über den ODBC-Treiber für Oracle-Setup:  
  
    -   **Übersetzung** -klicken Sie auf auswählen, wählen Sie einen Übersetzer geladenen Daten. Der Standardwert ist \<keine Translator >.  
  
    -   **Leistung** -der enthalten Hinweise im Kontrollkästchen Katalogfunktionen angibt, ob es sich bei gibt der Treiber "Hinweise"-Spalten für die [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) Resultset. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff auf, wenn dieser Wert nicht festgelegt ist.  
  
         Die SYNONYME sind Kontrollkästchen für die SQL-Spalten gibt an, ob der Treiber die Spalteninformationen zurückgegeben. **Puffergröße** gibt die Größe in Byte zugeordnet, um die abgerufene Daten zu erhalten. Der Treiber optimiert werden abgerufen, sodass einen Abruf aus der Oracle-Server genügend Zeilen für einen Puffer mit der angegebenen Größe füllen zurückgibt. Größere Werte sind tendenziell zu erhöhen, wenn eine große Datenmenge abrufen.  
  
    -   **Anpassung** – Kontrollkästchen im erzwingen ODBC DayOfWeek-Standard gibt an, ob das Resultset in das angegebene ODBC-Tag der Woche-Format entspricht (Sonntag = 1; Samstag = 7). Wenn dieses Kontrollkästchen deaktiviert ist, wird der Wert der Gebietsschema-spezifische Oracle zurückgegeben.  
  
         Die SQLDescribeCol **gibt immer einen Wert für Genauigkeit** Kontrollkästchen gibt an, und zwar unabhängig davon, ob der Treiber einen Wert ungleich NULL für zurückgeben soll die *CbColDef* Argument **SQLDescribeCol**. Dieses Verbindungszeichenfolgenattribut gilt nur für Spalten, in denen es keine Skalierung Oracle definiert, ist wie z. B. berechnete numerische, Spalten und Spalten als Zahl ohne eine Genauigkeit oder Dezimalstellenanzahl. Ein **SQLDescribeCol** für die Genauigkeit gibt 130 aufrufen, wenn Oracle diese Informationen nicht bereitstellt. Wenn dieses Kontrollkästchen deaktiviert ist, wird der Treiber stattdessen für diese Spaltentypen 0 zurück.  
  
2.  Klicken Sie auf Hinzufügen, um eine andere Datenquelle hinzuzufügen, oder klicken Sie auf Schließen, um zu beenden.  
  
### <a name="to-modify-a-data-source-for-windows"></a>So ändern Sie eine Datenquelle für Windows  
  
1.  Öffnen Sie die ODBC-Datenquellen-Administrator. Klicken Sie auf die entsprechende Registerkarte aus DSN.  
  
2.  Wählen Sie die Oracle-Datenquelle, die Sie ändern, und klicken Sie dann auf konfigurieren möchten. Microsoft ODBC für Oracle-Setup-Dialogfeld wird angezeigt.  
  
3.  Ändern Sie die entsprechenden Datenquellenfeldern, und klicken Sie dann auf OK.  
  
 Wenn Sie nach dem die Informationen in diesem Dialogfeld ändern, aktualisiert der ODBC-Administrator Informationen aus der Registrierung.
