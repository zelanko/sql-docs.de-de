---
title: Datenquellen-Assistent (Bildschirm 4); ODBC-Treiber für SQL Server | Microsoft-Dokumentation
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989466"
---
# <a name="data-source-wizard-screen-4"></a>Datenquellen-Assistent (Bildschirm 4)

Geben Sie die Sprache an, die für SQL Server-Meldungen verwendet werden soll, die Übersetzung des Zeichensatzes, und ob der ODBC Driver for SQL Server Einstellungen für Land/Region verwenden soll. Sie können auch die Protokollierung von Abfragen mit langer Ausführungszeit und die Einstellungen der Treiberstatistik steuern.

## <a name="options"></a>Tastatur

### <a name="change-the-language-of-sql-server-system-messages-to"></a>Ändern der Sprache von SQL Server-Systemmeldungen in

Jede Instanz von SQL Server kann mehrere Sätze an Systemmeldungen jeweils in einer anderen Sprache (z. B. Englisch, Spanisch, Französisch usw.) aufweisen. Wenn eine Datenquelle für einen bestimmten Server definiert ist, die mehrere Sätze an Systemmeldungen aufweist, können Sie angeben, welche Sprache für Systemmeldungen verwendet werden soll. Klicken Sie in der Liste auf die Sprache. Diese Option ist nicht verfügbar, wenn nur eine Sprache in SQL Server installiert ist.

### <a name="use-strong-encryption-for-data"></a>Starke Verschlüsselung für Daten verwenden

Wenn diese Option ausgewählt ist, werden Daten, die durch Verbindungen weitergeleitet werden, die mit diesem DSN hergestellt werden, verschlüsselt. Anmeldungen werden standardmäßig verschlüsselt, auch wenn das Kontrollkästchen deaktiviert wird.

### <a name="trust-server-certificate"></a>Serverzertifikat vertrauen

Diese Option ist nur verfügbar, wenn die Option **Starke Verschlüsselung für Daten verwenden** aktiviert ist. Wenn Sie diese Option auswählen, wird nicht geprüft, ob das Zertifikat den richtigen Hostnamen des Servers hat und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt wurde. 

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

Gibt an, wie oft versucht werden soll, einen erfolglosen Verbindungsversuch zu wiederholen

### <a name="connect-retry-interval-seconds"></a>Verbindungswiederholungsintervall (Sekunden)

Gibt an, wie viele Sekunden zwischen den einzelnen Verbindungsversuchen liegen sollen. Weitere Informationen zur Verwendung dieser Option und der Option **Verbindungswiederholungsanzahl** finden Sie unter [Verbindungsresilienz im ODBC-Treiber für Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).

### <a name="back"></a>Zurück

Klicken Sie auf diese Schaltfläche, um zur vorherigen Seite des Assistenten zurückzukehren.

### <a name="finish"></a>Finish

Nachdem Sie auf diesem Bildschirm alle Informationen angegeben haben, klicken Sie auf **Finish** (Fertigstellen). Der DSN wird erstellt. Dabei werden alle Attribute verwendet, die Sie auf dieser und auf den anderen Seiten des Assistenten angegeben haben. Anschließend haben Sie die Möglichkeit, den neu erstellten DSN zu testen.

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 3)](../../../connect/odbc/windows/dsn-wizard-3.md)
