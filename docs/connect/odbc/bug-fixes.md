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
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 2b939db6ac0f89075b39ba74eadb0e86e63e3980
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041222"
---
# <a name="list-of-bugs-fixed"></a>Liste der behobenen Fehler

Diese Seite enthält eine Liste von Fehlern, die in jeder Version behoben werden, beginnend mit [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-1742-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen im [!INCLUDE[msCoName](../../includes/msconame_md.md)]-ODBC-Treiber 17.4.2 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

 - Behebung eines Problems, bei dem die Prozess-ID und der Anwendungsname nicht ordnungsgemäß an SQL Server gesendet werden (für sys. DM _exec_sessions Analysis) (Linux)
 - Entfernte redundante Abhängigkeit von libuuid (Linux)
 - Behebung eines Fehlers beim Senden von UTF8-Daten an SQL Server 2019
 - Behebung eines Fehlers, bei dem Gebiets Schemas, die auf "@euro" enden, nicht ordnungsgemäß erkannt wurden (Linux)
 - Korrektur für XML-Daten, die fälschlicherweise zurückgegeben werden, wenn Sie als Output-Parameter abgerufen werden, wenn Always Encrypted

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-174-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen im [!INCLUDE[msCoName](../../includes/msconame_md.md)]-ODBC-Treiber 17,4 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Behebung von zeitweiligen hängen, wenn mehrere aktive Resultsets (Mars) aktiviert sind
- Beheben Sie die Verbindungs Resilienz, wenn die asynchrone Benachrichtigung aktiviert ist.
- Behebung eines Absturzes beim Abrufen von Diagnosedaten Sätzen für Multithread-Verbindungsversuche
- Die Korrektur "Verschlüsselung wird nicht unterstützt" beim erneuten Herstellen der Verbindung nach dem Aufruf von SQLGetInfo () mit SQL_USER_NAME und SQL_DATA_SOURCE_READ_ONLY
- Beheben eines com-Initialisierungs Fehlers während Azure Active Directory interaktiven Authentifizierung
- Korrigieren von SQLGetData () für mehr Byte-UTF8-Daten
- Korrektur beim Abrufen der Länge von sql_variant-Spalten mit SQLGetData ()
- Korrigieren des Importierens von sql_variant-Spalten mit mehr als 7992 Bytes mithilfe von bcp
- Korrektur des Sendevorgangs für die korrekte Codierung an den Server für schmale Zeichendaten

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen im [!INCLUDE[msCoName](../../includes/msconame_md.md)]-ODBC-Treiber 17,3 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Korrigieren des Speicherlecks für das TCP-Sende Benachrichtigungs Ereignis
- Behobene neudefinitions Problem der Enumeration-_SQL_FILESTREAM_DESIRED_ACCESS in der msodbcsql. h-Header Datei
- Korrigiert: fehlende ACCESS_TOKEN und Authentifizierungs bezogene Definition in der msodbcsql. h-Header Datei für Linux

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen im [!INCLUDE[msCoName](../../includes/msconame_md.md)]-ODBC-Treiber 17,2 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Es wurde eine Fehlermeldung zur Azure Active Directory Authentifizierung korrigiert.
- Korrigieren der Codierungs Erkennung, wenn Gebiets Schema Umgebungsvariablen anders festgelegt werden
- Es wurde ein Absturz beim Trennen der Verbindung mit der Verbindungs Wiederherstellung korrigiert.
- Erkennung der Verbindungs Zulässigkeit korrigiert
- Fehlerhafte Erkennung geschlossener Sockets korrigiert
- Beim Versuch, ein Anweisungs Handle bei einer fehlgeschlagenen Wiederherstellung freizugeben
- Es wurde ein falsches uninstallationsverhalten korrigiert, wenn sowohl Version 13 als auch 17 unter Windows installiert sind.
- Festes Entschlüsselungs Verhalten auf älterer Windows-Plattform (Windows 7, 8 und Server 2012)
- Korrigiert eines Cache Problems bei Verwendung der Adal-Authentifizierung unter Windows
- Es wurde ein Problem behoben, bei dem Ablauf Verfolgungs Protokolle unter Windows gesperrt und überschrieben wurden.

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen im [!INCLUDE[msCoName](../../includes/msconame_md.md)]-ODBC-Treiber 17,1 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Eine Verzögerung von 1 Sekunde wurde beim Aufrufen von SQLFreeHandle mit aktiviertem Mars und dem Verbindungs Attribut "verschlüsseln = ja" korrigiert.
- Es wurde ein Absturz von Fehler 22003 in SQLGetData korrigiert, wenn die Puffergröße kleiner ist als die abgerufenen Daten (Windows).
- Abgeschnittene Adal-Fehlermeldungen korrigiert
- Es wurde ein seltener Fehler auf 32-Bit-Fenstern behoben, wenn eine Gleit Komma Zahl in eine ganze Zahl umgerechnet wurde.
- Es wurde ein Problem behoben, bei dem das Einfügen von Double in das Decimal-Feld mit der Always Encrypted on-Datei zu einem
- Eine Warnung für den MacOS-Installer wurde korrigiert.
- Das Senden eines falschen Zustands an den SQL Server während des Wiederherstellungs Versuchs der Sitzung wurde korrigiert, wenn die verbindungsresilienz und das Verbindungs Pooling aktiviert sind, sodass die Sitzung vom Server gelöscht wird.

### <a name="bug-fixes-in-the-includemsconameincludesmsconame_mdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Fehlerbehebungen in der [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Ein Fehler wurde behoben, bei dem bei Verwendung der Kerberos-Authentifizierung Massen Einfügung mit dem Fehler "Zugriff verweigert" fehlgeschlagen ist.
- Problem Umgehung für einen unixodbc-Fehler in Version unten 2.3.1 entfernt (der Treiber hat die Größe bestimmter an unixodbc übergebenen Puffer verdoppelt)
- Verbindungs Resilienz (Verbindung wiederherstellen) mit aktiviertem columnencryption = wurde korrigiert
- Behobene DSN-Erstellungs Fehler: bei Verwendung der Option "Active Directory interaktive Authentifizierung" konnte das Azure-Authentifizierungs Fenster nicht mehr reagiert (Windows).
- Es wurde ein seltener Absturz beim Herunterfahren von ODBC korrigiert, wenn die asynchrone Ausführung aktiviert ist (beim Löschen des Verbindungs Handles).
- Ein Problem wurde behoben, bei dem der SQL-Treiber beim Ausführen langer gespeicherter Prozeduren eine hohe CPU
- Fehler beim Abrufen von Daten in einer verschlüsselten varbinary (max)-Spalte ohne Konvertierung.
- Es wurde ein Problem behoben, bei dem nach dem Abrufen der verschlüsselten Spalte "varchar (max)" mit SQLGetData () in einem statischen Cursor die folgende Spalte ebenfalls NULL ist, auch wenn Sie über Daten verfügt.
- Es wurde ein Problem behoben, beim Abrufen des varbinary (max)-Felds mit Always Encrypted on
- Es wurde ein Problem behoben, das setlocale () nicht mit Always Encrypted arbeitet.
- Es wurde ein Problem behoben, bei dem SQLDescribeParam () einen Fehler zurückgibt, wenn der Parameter für gespeicherte Prozeduren von XML-Typen mit Always Encrypted
- Korrigiert mit Escapezeichen, die nicht in SQLTables funktionieren
- Es wurde ein Fehler behoben, bei dem hebräische Daten (varchar) abgeschnitten werden, wenn Sie als Wide Zeichen unter Linux zurückgegeben werden.
- Es wurde ein Problem behoben, das das Abfragen von Shift-JIS-codiertem char/varchar aus der UTF-8-Anwendung
- Es wurde ein Fehler behoben, bei dem der Aufruf von SQLGetInfo mit dem Parameter "SQL_DRIVER_NAME" im Linux-Format unter MacOS
- Es wurde ein Problem behoben, bei dem das Laden von Windows-1252-Zeichendaten mithilfe von Eingabedateien mit mehr als 32 KB in varchar-Spalten mit dem Hilfsprogramm bcp zu Fehlern führen würde.
