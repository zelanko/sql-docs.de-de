---
title: Hinzufügen und Ändern von Datenquellen mithilfe von Setup | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281410"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Erstellen und Ändern von Datenquellen mithilfe der Einrichtung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Eine Datenquelle identifiziert einen Pfad zu Daten, die eine Netzwerk Bibliothek, einen Server, eine Datenbank und andere Attribute enthalten können. in diesem Fall ist die Datenquelle der Pfad zu einer Oracle-Datenbank. Zum Herstellen einer Verbindung mit einer Datenquelle prüft der Treiber-Manager die Windows-Registrierung auf bestimmte Verbindungsinformationen.  
  
 Der vom ODBC-Datenquellen-Administrator erstellte Registrierungs Eintrag wird vom ODBC-Treiber-Manager und von ODBC-Treibern verwendet. Dieser Eintrag enthält Informationen zu den einzelnen Datenquellen und den zugehörigen Treibern. Bevor Sie eine Verbindung mit einer Datenquelle herstellen können, müssen die zugehörigen Verbindungsinformationen der Registrierung hinzugefügt werden.  
  
 Verwenden Sie zum Hinzufügen und Konfigurieren von Datenquellen den [ODBC-Daten](../../odbc/admin/odbc-data-source-administrator.md)Quellen-Administrator. Der ODBC-Administrator aktualisiert die Verbindungsinformationen für die Datenquelle. Wenn Sie Datenquellen hinzufügen, aktualisiert der ODBC-Administrator die Registrierungsinformationen für Sie.  
  
### <a name="to-add-a-data-source-for-windows"></a>So fügen Sie eine Datenquelle für Windows hinzu  
  
1.  Öffnen Sie den ODBC-Datenquellen-Administrator.  
  
2.  Klicken Sie im Dialogfeld ODBC-Datenquellen-Administrator auf hinzufügen. Das Dialogfeld neue Datenquelle wird angezeigt.  
  
3.  Wählen Sie Microsoft ODBC für Oracle aus, und klicken Sie auf Fertigstellen. Das Setup Dialogfeld für Microsoft ODBC für Oracle wird angezeigt.  
  
4.  Geben Sie im Feld Datenquellen Name den Namen der Datenquelle ein, auf die Sie zugreifen möchten. Dies kann ein beliebiger Name sein, den Sie auswählen.  
  
5.  Geben Sie im Feld Beschreibung die Beschreibung für den Treiber ein. In diesem optionalen Feld wird der Datenbanktreiber beschrieben, mit dem die Datenquelle eine Verbindung herstellt. Dies kann ein beliebiger Name sein, den Sie auswählen.  
  
6.  Geben Sie im Feld Benutzername Ihren Datenbankbenutzer Namen (Ihre Datenbank-Benutzer-ID) ein.  
  
7.  Geben Sie im Feld Server den Datenbankalias oder die Verbindungs Zeichenfolge für die Oracle-Server-Engine ein, auf die Sie zugreifen möchten.  
  
8.  Klicken Sie auf OK, um diese Datenquelle hinzuzufügen.  
  
> [!NOTE]  
>  Das Dialogfeld Datenquellen wird angezeigt, und der ODBC-Administrator aktualisiert die Registrierungsinformationen. Der Benutzername und die Verbindungs Zeichenfolge, die Sie eingegeben haben, werden als Standard Verbindungs Werte für diese Datenquelle angezeigt, wenn Sie eine Verbindung damit herstellen.  
  
1.  Klicken Sie auf Optionen, um weitere Spezifikationen zum ODBC-Treiber für Oracle-Setup zu erstellen:  
  
    -   **Übersetzung** : Klicken Sie auf auswählen, um einen geladenen Datenkonvertierer auszuwählen. Der Standardwert \<ist kein Konvertierungs>.  
  
    -   **Leistung** : das Kontrollkästchen "Hinweise in Katalog Funktionen einschließen" gibt an, ob der Treiber Hinweise Spalten für das [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) -Resultset zurückgibt. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.  
  
         Das Kontrollkästchen Synonyme in SQL-Spalten einschließen gibt an, ob der Treiber Spalten Informationen zurückgibt. **Puffergröße** gibt die Größe in Bytes an, die zum Empfangen von abgerufenen Daten zugeordnet ist. Der Treiber optimiert das Abrufen, sodass ein Abruf vom Oracle-Server genügend Zeilen zurückgibt, um einen Puffer mit der angegebenen Größe auszufüllen. Größere Werte verbessern tendenziell die Leistung, wenn Sie viele Daten abrufen.  
  
    -   **Anpassung** : das Kontrollkästchen ODBC DayOfWeek Standard erzwingen gibt an, ob das Resultset dem von ODBC angegebenen Tag-of-week-Format entsprechen soll (Sonntag = 1; Samstag = 7). Wenn dieses Kontrollkästchen deaktiviert ist, wird der Gebiets Schema spezifische Oracle-Wert zurückgegeben.  
  
         Das Kontrollkästchen SQLDescribeCol **gibt immer einen Wert für die Genauigkeit zurück** . gibt an, ob der Treiber einen Wert ungleich 0 (null) für das *cbcoldef* -Argument von **SQLDescribeCol**zurückgeben soll. Dieses Verbindungs Zeichen folgen Attribut gilt nur für Spalten, bei denen keine Oracle-definierte Skala vorhanden ist, z. b. berechnete numerische Spalten und Spalten, die als Zahl ohne Genauigkeit oder Dezimalstelle definiert sind. Ein **SQLDescribeCol** -Befehl gibt 130 für die Genauigkeit zurück, wenn Oracle diese Informationen nicht bereitstellt. Wenn dieses Kontrollkästchen deaktiviert ist, gibt der Treiber stattdessen 0 für diese Spaltentypen zurück.  
  
2.  Klicken Sie auf Hinzufügen, um eine weitere Datenquelle hinzuzufügen, oder klicken Sie zum Beenden auf  
  
### <a name="to-modify-a-data-source-for-windows"></a>So ändern Sie eine Datenquelle für Windows  
  
1.  Öffnen Sie den ODBC-Datenquellen-Administrator. Klicken Sie auf die entsprechende Registerkarte DSN.  
  
2.  Wählen Sie die zu ändernde Oracle-Datenquelle aus, und klicken Sie dann auf konfigurieren. Das Setup Dialogfeld für Microsoft ODBC für Oracle wird angezeigt.  
  
3.  Ändern Sie die entsprechenden Datenquellen Felder, und klicken Sie dann auf OK.  
  
 Nachdem Sie die Informationen in diesem Dialogfeld geändert haben, aktualisiert der ODBC-Administrator die Registrierungsinformationen.
