---
title: Liste der behobenen Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 6ef479b95e62c2f489b06905b33318a877a60ad5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784003"
---
# <a name="list-of-bugs-fixed"></a>Liste der behobenen Fehler

Diese Seite enthält eine Auflistung der behobenen Probleme in jeder Version, beginnend mit [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerkorrekturen in der [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC-Treiber 17.2 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Korrigiert eine Fehlermeldung über Azure Active Directory-Authentifizierung
- Feste Codierung erkennen, die Gebietsschema-Umgebungsvariablen sind anders festgelegt
- Feste ein Absturzes beim Trennen, mit der Wiederherstellung der Verbindung wird ausgeführt
- Korrektur der Erkennung von Verbindung Verfügbarkeitseigenschaften
- Korrektur der falschen Erkennung von geschlossenen sockets
- Korrigiert eine unendliche Wartezeit an, beim Freigeben eines Anweisungshandles während der fehlerhaften Wiederherstellung
- Korrigiert falsche Deinstallation Verhalten, wenn sowohl Version 13 und 17 für Windows installiert sind
- Feste Entschlüsselung-Verhalten in älteren Windows-Plattform (Windows 7, 8 und Server 2012)
- Ein Cache-Problem wurde behoben, bei Verwendung von ADAL-Authentifizierung für Windows
- Das Sperren wurde das Problem wurde behoben, und überschreiben die Ablaufverfolgung auf Windows-Protokolle

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerkorrekturen in der [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC-Treiber 17.1 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- 1-Sekunden Verzögerung behoben, Aufrufen von SQLFreeHandle bei aktivierter MARS- und -Verbindungsattribut "Encrypt = Yes"
- Korrektur einer Fehler 22003 Absturzes in SQLGetData, wenn die Größe des übergebenen Puffers kleiner ist und die Daten abgerufen werden (Windows)
- Abgeschnittene ADAL Fehlermeldungen korrigiert
- Auf 32-Bit-Windows behoben seltenen Fehler, bei der Konvertierung eine Gleitkommazahl Zahl in eine ganze Zahl
- Ein Problem wurde behoben, in dem Einfügen in Feld "decimal" mit Always Encrypted auf doppelte datenabschneidefehler zurück
- "Fixed" eine Warnung auf MacOS-installer
- Feste senden falschen Status auf SQL Server während der Sitzung Wiederherstellungsversuch ein, wenn die Resilienz von Verbindungen und Verbindungspooling beide aktiviert sind und verursacht die Sitzung vom Server gelöscht werden soll,

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerkorrekturen in der [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Korrektur eines Fehlers, bei Verwendung der Kerberos-Authentifizierung masseneinfügung mit "Zugriff verweigert"-Fehler ausfallen
- Entfernte behelfslösung für einen UnixODBC-Fehler, die in die ältere Version 2.3.1 vorhanden (verdoppelt, die Größe der bestimmten Puffer übergeben, um den UnixODBC Treiber)
- Verbindungsresilienz behoben (Verbinden) hängt von der Verwendung ColumnEncryption = aktiviert
- DSN-Erstellung-Fehler, behoben, wenn "Interaktive Active Directory-Authentifizierung" mit option Azure Authentication kann Fenster nicht mehr reagiert (Windows) werden
- Seltenen Absturz behoben während des Herunterfahrens auf ODBC, wenn die asynchrone Ausführung (aufgetreten ist, wenn Verbindungshandle deaktivieren) aktiviert ist
- Ein Problem wurde behoben, in dem SQL-Treiber hohe CPU-Auslastung beim Ausführen gespeicherter Prozeduren verursacht
- Feste kann zum Abrufen von Daten in einer verschlüsselten varbinary(max)-Spalte ohne Konvertierung
- Ein Problem behoben, in dem nach einem null-varchar(max) verschlüsselten Spalten abgerufen SQLGetData() in einem statischen Cursor verwenden, wird die folgende Spalte ebenfalls NULL gesetzt, auch wenn sie Daten enthält
- Behebung eines Problems mit 'varbinary(max)'-Feld mit Always Encrypted auf Abrufen
- Behebt ein Problem der setlocale() funktioniert nicht mit Always Encrypted
- Behebung eines Problems mit SQLDescribeParam() Fehler bei Aufruf in XML-Datentyp gespeicherten Prozedurparameter mit Always Encrypted in zurückgegeben
- Feste mit Escapezeichen Unterstriche im SQLTables nicht funktioniert.
- Korrektur eines Fehlers, in dem hebräische Daten (Varchar) abgeschnitten als Breitzeichen unter Linux zurückgegeben
- Korrigiert: beim Abfragen der Shift-JIS codiert Char/Varchar aus UTF-8-Anwendung
- Der Fehler behoben, der Speicherort für die Rückgabe SQLGetInfo mit SQL_DRIVER_NAME Parameter aufrufen Dateiname des Linux-Stil unter MacOS
- Ein Problem wurde behoben, in denen Dateien laden Sie Windows-1252-Zeichendaten, die mit der Eingabe von mehr als 32 KB, die Bytes in den VARCHAR-Spalten, die mit dem BCP-Hilfsprogramm zu Fehlern führen würde
