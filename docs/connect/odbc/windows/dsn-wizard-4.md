---
title: Datenquellen-Assistent (Bildschirm 4) (ODBC-Treiber für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 177888dd1034bb1edcb870db38b00bbc418cb261
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989466"
---
# <a name="data-source-wizard-screen-4"></a>Datenquellen-Assistent (Bildschirm 4)

Geben Sie die Sprache an, die für SQL Server-Meldungen verwendet werden soll, die Übersetzung des Zeichensatzes, und ob der ODBC Driver for SQL Server Einstellungen für Land/Region verwenden soll. Sie können auch die Protokollierung von Abfragen mit langer Ausführungszeit und die Einstellungen der Treiberstatistik steuern.

## <a name="options"></a>enthalten

### <a name="change-the-language-of-sql-server-system-messages-to"></a>Ändern der Sprache von SQL Server-Systemmeldungen in

Jede Instanz von SQL Server kann mehrere Sätze an Systemmeldungen jeweils in einer anderen Sprache (z. B. Englisch, Spanisch, Französisch usw.) aufweisen. Wenn eine Datenquelle für einen bestimmten Server definiert ist, die mehrere Sätze an Systemmeldungen aufweist, können Sie angeben, welche Sprache für Systemmeldungen verwendet werden soll. Klicken Sie in der Liste auf die Sprache. Diese Option ist nicht verfügbar, wenn nur eine Sprache in SQL Server installiert ist.

### <a name="use-strong-encryption-for-data"></a>Starke Verschlüsselung für Daten verwenden

Wenn diese Option ausgewählt ist, werden Daten, die durch Verbindungen weitergeleitet werden, die mit diesem DSN hergestellt werden, verschlüsselt. Anmeldungen werden standardmäßig verschlüsselt, auch wenn das Kontrollkästchen deaktiviert wird.

### <a name="trust-server-certificate"></a>Serverzertifikat vertrauen

Diese Option ist nur anwendbar, wenn die Option **starke Verschlüsselung für Daten verwenden** aktiviert ist. Wenn diese Option ausgewählt ist, wird das Zertifikat des Servers nicht so überprüft, dass es den richtigen Hostnamen des Servers hat und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt wird. 

### <a name="perform-translation-for-character-data"></a>Übersetzung für Zeichendaten ausführen

Wenn dieses Kästchen aktiviert wird, konvertiert der ODBC Driver for SQL Server ANSI-Zeichenfolgen, die zwischen dem Clientcomputer und SQL Server gesendet werden, mit Unicode. Der ODBC-Treiber führt manchmal Konvertierungen zwischen der SQL Server-Codepage und Unicode auf dem Clientcomputer aus. Dies erfordert, dass die von SQL Server verwendete Codepage eine der auf dem Clientcomputer verfügbaren Codepages ist.

Wenn dieses Kontrollkästchen deaktiviert wird, erfolgt keine Übersetzung von Sonderzeichen in ANSI-Zeichenfolgen, wenn sie zwischen der Clientanwendung und dem Server gesendet werden. Wenn der Clientcomputer eine andere ANSI-Codepage (ACP) als die SQL Server-Codepage verwendet, können Sonderzeichen in ANSI-Zeichenfolgen falsch interpretiert werden. Wenn der Clientcomputer dieselbe Codepage für seine ACP verwendet wie SQL Server, werden die Sonderzeichen ordnungsgemäß interpretiert.

### <a name="use-regional-settings-when-outputting-currency-numbers-dates-and-times"></a>Einstellungen für Land/Region für die Ausgabe von Währung, Zahlen, Datumsangaben und Uhrzeiten verwenden

Gibt an, dass der Treiber die Einstellungen des Clientcomputers für Land/Region für das Formatieren von Währung, Zahlen, Datumsangaben und Uhrzeiten, Datums- und Zeitdaten in ausgegebenen Zeichenfolgen verwenden soll. Der Treiber verwendet die Standardeinstellungen für Land/Region für das Windows-Anmeldekonto des Benutzers bei der Herstellung einer Verbindung durch die Datenquelle. Aktivieren Sie diese Option für Anwendungen, die Daten nur anzeigen, nicht für Anwendungen, die Daten verarbeiten.

### <a name="save-long-running-queries-to-the-log-file"></a>Abfragen mit langer Ausführungszeit in der Protokolldatei speichern

Gibt an, dass der Treiber jede Abfrage protokolliert, deren Ausführungszeit länger ist als der Wert für eine **lange Abfragezeit**. Abfragen mit langer Ausführungszeit werden in der angegebenen Datei protokolliert. Zum Angeben einer Protokolldatei geben Sie entweder den vollständigen Pfad und den Dateinamen in dem Feld an, oder klicken Sie auf **Durchsuchen**, um eine Protokolldatei durch Navigieren durch vorhandene Dateiverzeichnisse auszuwählen.

### <a name="long-query-time-milliseconds"></a>Lange Abfragezeit (Millisekunden)

Gibt einen Schwellenwert in Millisekunden für die Protokollierung von Abfragen mit langer Ausführungszeit an. Es wird jede Abfrage protokolliert, deren Ausführung länger dauert als diese Anzahl von Millisekunden.

### <a name="log-odbc-driver-statistics-to-the-log-file"></a>ODBC-Treiber-Statistik in der Protokolldatei protokollieren

Gibt an, dass die Statistik protokolliert werden soll. Die Statistik wird in der angegebenen Datei protokolliert. Zum Angeben einer Protokolldatei geben Sie entweder den vollständigen Pfad und den Dateinamen in dem Feld an, oder klicken Sie auf **Durchsuchen**, um eine Protokolldatei durch Navigieren durch vorhandene Dateiverzeichnisse auszuwählen.

Das Statistikprotokoll ist eine durch Tabstopps getrennte Datei, die in Microsoft Excel oder in jeder anderen Anwendung analysiert werden kann, die durch Tabstopps getrennte Dateien unterstützt.

### <a name="connect-retry-count"></a>Verbindungswiederholungsanzahl

Gibt an, wie oft versucht wird, einen erfolglosen Verbindungsversuch zu wiederholen.

### <a name="connect-retry-interval-seconds"></a>Verbindungswiederholungsintervall (Sekunden)

Gibt die Anzahl der Sekunden zwischen den einzelnen Verbindungs Wiederholungs versuchen an. Weitere Informationen zu diesem Vorgang und den Optionen für die Verbindungs **Wiederholungs Anzahl finden Sie** unter [verbindungsresilienz im Windows ODBC-Treiber](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).

### <a name="back"></a>Zurück

Klicken Sie auf diese Schaltfläche, um zur vorherigen Seite des Assistenten zurückzukehren.

### <a name="finish"></a>Fertig stellen

Wenn die auf diesem Bildschirm angegebenen Informationen vollständig sind, können Sie auf **Fertig**stellen klicken. Der DSN wird mit allen auf diesem und anderen Bildschirmen des Assistenten angegebenen Attributen erstellt, und Sie haben die Möglichkeit, den neu erstellten DSN zu testen.

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 3)](../../../connect/odbc/windows/dsn-wizard-3.md)
