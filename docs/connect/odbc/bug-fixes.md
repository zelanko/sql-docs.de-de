---
title: Liste der behobenen Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-chojas
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: e1be25052ed75370eead58832119d543717b8e16
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896778"
---
# <a name="list-of-bugs-fixed"></a>Liste der behobenen Fehler

Auf dieser Seite werden alle Fehler aufgeführt, die beginnend mit [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in jeder Version behoben wurden.

### <a name="bug-fixes-in-the-msconame-odbc-driver-1752-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.5.2 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- „msodbcsql.h“ zum Alpine Linux-Paket hinzugefügt

### <a name="bug-fixes-in-the-msconame-odbc-driver-175-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.5 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Korrektur der AKV-CMK-Metadaten-Hashberechnung unter Linux/Mac
- Behebung eines Fehlers beim Laden von OpenSSL 1.0.0
- Behebung von Konvertierungsproblemen bei Verwendung von ISO-8859-1- und ISO-8859-2-Codepages
- Korrektur des internen Bibliotheksnamens unter Mac zum Einschluss der Versionsnummer
- Korrektur der Einstellung des NULL-Indikators, wenn separate Längen- und Indikatorbindungen verwendet werde

### <a name="bug-fixes-in-the-msconame-odbc-driver-1742-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.4.2 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

 - Behebung eines Problems, bei dem die Prozess-ID und der Anwendungsname nicht ordnungsgemäß an SQL Server gesendet werden (zur Analyse von „sys.dm_exec_sessions“) (Linux)
 - Redundante Abhängigkeit in „libuuid“ entfernt (Linux)
 - Behebung eines Fehlers beim Senden von UTF8-Daten an SQL Server 2019
 - Korrektur eines Fehlers, durch den Gebietsschemas, die auf „@euro“ enden, nicht ordnungsgemäß erkannt wurden (Linux)
 - Korrektur für XML-Daten, die beim Abruf als Ausgabeparameter während der Verwendung von Always Encrypted falsch zurückgegeben werden

### <a name="bug-fixes-in-the-msconame-odbc-driver-174-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.4 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Behebung von zeitweiligen Reaktionsverlusten, wenn Multiple Active Results Sets (MARS) aktiviert ist
- Behebung von Problemen mit der Verbindungsresilienz, wenn die asynchrone Benachrichtigung aktiviert ist
- Absturz beim Abruf von Diagnosedatensätzen für Verbindungsversuche mit Multithreading behoben
- Behebung des Fehlers „Verschlüsselung nicht unterstützt“ bei der erneuten Verbindungsherstellung nach dem Aufruf von SQLGetInfo() mit SQL_USER_NAME und SQL_DATA_SOURCE_READ_ONLY
- Korrektur eines COM-Initialisierungsfehlers während der interaktiven Azure Active Directory-Authentifizierung
- Korrektur von SQLGetData() für Multibyte-UTF8-Daten
- Korrektur für den Längenabruf von sql_variant-Spalten mit SQLGetData()
- Korrektur für den Import von sql_variant-Spalten mit mehr als 7992 Bytes über BCP
- Korrektur für das Senden der richtigen Codierung an den Server für schmale Zeichendaten

### <a name="bug-fixes-in-the-msconame-odbc-driver-173-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Ereignishandle-Speicherleck bei TCP-Sendebenachrichtigung behoben
- Korrektur eines Problems beim Neudefinieren der Enumeration _SQL_FILESTREAM_DESIRED_ACCESS in der Headerdatei „msodbcsql.h“
- Fehlende ACCESS_TOKEN- und AUTHENTICATION-Definition in der Headerdatei „msodbcsql.h“ für Linux behoben

### <a name="bug-fixes-in-the-msconame-odbc-driver-172-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Korrektur einer Fehlermeldung zur Azure Active Directory-Authentifizierung
- Korrektur der Codierungserkennung, wenn lokale Umgebungsvariablen unterschiedlich festgelegt sind
- Absturz beim Trennen der Verbindung bei laufender Verbindungswiederherstellung behoben
- Korrektur der Erkennung der Verbindungsaktivität
- Falsche Erkennung geschlossener Sockets behoben
- Fehlerbehebung für unendliche Wartezeit beim Versuch, ein Anweisungshandle während einer fehlerhaften Wiederherstellung freizugeben
- Korrektur eines falschen Deinstallationsverhaltens, wenn sowohl Version 13 als auch Version 17 unter Windows installiert sind
- Korrektur des Entschlüsselungsverhaltens auf älteren Windows-Plattformen (Windows 7, 8 und Server 2012)
- Behebung eines Cacheproblems bei Verwendung der ADAL-Authentifizierung unter Windows
- Behebung eines Problems, durch das Ablaufverfolgungsprotokolle unter Windows gesperrt und überschrieben wurden

### <a name="bug-fixes-in-the-msconame-odbc-driver-171-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Verzögerung von 1 Sekunde beim Aufruf von SQLFreeHandle mit aktiviertem MARS und Verbindungsattribut „Encrypt=yes“ behoben
- Absturz mit Fehler 22003 in SQLGetData behoben, wenn der übergebene Puffer kleiner ist als die abzurufenden Daten (Windows)
- Korrektur abgeschnittener ADAL-Fehlermeldungen
- Korrektur eines seltenen Fehlers unter 32-Bit-Windows bei der Konvertierung einer Gleitkommazahl in eine Ganzzahl
- Behebung eines Problems, bei dem das Einfügen eines double-Werts in ein Dezimalfeld bei aktivierter Option „Always Encrypted“ einen Fehler aufgrund von abgeschnittenen Daten verursachte
- Korrektur einer Warnung im macOS-Installer
- Behebung eines Fehlers, durch den während des Versuchs der Sitzungswiederherstellung ein falscher Status an SQL Server gesendet wurde, wenn sowohl die Verbindungsresilienz als auch das Verbindungspooling aktiviert waren, was zum Abbruch der Sitzung durch den Server führte

### <a name="bug-fixes-in-the-msconame-odbc-driver-17-for-ssnoversion"></a>Fehlerbehebungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Behebung eines Fehlers, durch den ein Masseneinfügevorgang bei aktivierter Kerberos-Authentifizierung zu einem Fehler „Zugriff verweigert“ führen konnte
- Umgehung für einen unixODBC-Fehler in Versionen vor 2.3.1 entfernt (Treiber verdoppelte die Größe bestimmter Puffer, die an unixODBC übergeben wurden)
- Reaktionsverlust bei Verbindungsresilienz (erneute Verbindung) bei Verwendung von ColumnEncryption=enabled behoben
- Behebung eines Fehlers bei der DSN-Erstellung, durch den bei Verwendung der Option „Interaktive Active Directory-Authentifizierung“ das Fenster „Azure-Authentifizierung“ möglicherweise nicht mehr reagierte (Windows)
- Behebung eines seltenen Absturzes während des Herunterfahrens von ODBC bei aktivierter asynchroner Ausführung (Fehler trat beim Löschen des Verbindungshandles auf)
- Behebung eines Problems, bei dem der SQL-Treiber während der Ausführung gespeicherter Prozeduren mit langer Laufzeit eine hohe CPU-Auslastung verursachte
- Korrektur eines Fehlers, durch den Daten in einer verschlüsselten varbinary(max)-Spalte ohne Konvertierung nicht abgerufen werden konnten
- Behebung eines Problems, bei dem nach dem Abrufen einer auf NULL festgelegten verschlüsselten varchar(max)-Spalte mittels SQLGetData() für einen statischen Cursor auch die folgende Spalte auf NULL festgelegt wird, selbst wenn sie Daten enthält
- Korrektur eines Problems beim Abrufen eines varbinary(max)-Felds mit aktivierter Option „Always Encrypted“
- Korrektur eines Problems, durch das setlocale() nicht ordnungsgemäß mit der Option „Always Encrypted“ funktioniert
- Behebung eines Problems mit SQLDescribeParam(), das zu einem Fehler führte, wenn ein Parameter einer gespeicherten Prozedur vom Typ „XML“ bei aktivierter Option „Always Encrypted“ aufgerufen wurde
- Korrektur von Unterstrichen mit Escapezeichen, die in SQLTables nicht funktionieren
- Korrektur eines Fehlers, durch den hebräische Daten (varchar) bei Rückgabe als breite Zeichen unter Linux abgeschnitten wurden
- Korrektur eines Problems mit der Abfrage von Shift-JIS-codierten char/varchar-Daten aus einer UTF8-Anwendung
- Behebung eines Fehlers, durch den der Aufruf von SQLGetInfo mit dem Parameter SQL_DRIVER_NAME unter macOS einen Dateinamen im Linux-Stil zurückgab
- Behebung eines Problems, das beim Laden von Windows-1252-Zeichendaten unter Verwendung von Eingabedateien mit mehr als 32.000 Byte in VARCHAR-Spalten unter Verwendung des BCP-Dienstprogramms zu Fehlern führte
