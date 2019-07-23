---
title: Ablaufverfolgung des Datenzugriffs mit dem ODBC-Treiber unter Linux und macOS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fa39cd11f70a661de5c284e56f2ccc0f7a5777f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008819"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Datenzugriffs-Ablaufverfolgung mit dem ODBC-Treiber unter Linux und macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der unixodbc-Treiber-Manager unter macOS und Linux unterstützt die Ablauf Verfolgung von ODBC-API-Aufrufe und das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Beenden des ODBC-Treibers für.

Um das ODBC-Verhalten Ihrer Anwendung zu verfolgen, `odbcinst.ini` bearbeiten Sie `[ODBC]` den Abschnitt der Datei, `Trace=Yes` um `TraceFile` die Werte und den Pfad der Datei festzulegen, die die Ausgabe der Ablauf Verfolgung enthalten soll. Beispiel:

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Sie können auch oder `/dev/stdout` einen beliebigen anderen Gerätenamen verwenden, um die Ausgabe der Ablauf Verfolgung an dieser Stelle statt an eine persistente Datei zu senden.) Mit den oben genannten Einstellungen werden bei jedem Laden der unixodbc-Treiber-Manager-Anwendung alle ODBC-API-Aufrufe aufgezeichnet, die in der Ausgabedatei ausgeführt wurden.

Entfernen `Trace=Yes` Sie nach Abschluss der Ablauf Verfolgung Ihrer Anwendung aus `odbcinst.ini` der Datei, um die Leistungseinbußen bei der Ablauf Verfolgung zu vermeiden, und stellen Sie sicher, dass unnötige Ablauf Verfolgungs Dateien entfernt werden.

Die Ablaufverfolgung gilt für alle Anwendungen, die den Treiber in `odbcinst.ini` verwenden. Um nicht alle Anwendungen zu verfolgen (z.B., damit benutzerbezogene vertrauliche Informationen nicht weitergegeben werden), können Sie eine einzelne Anwendungsinstanz verfolgen, indem Sie den Speicherort einer privaten `odbcinst.ini`-Datei mit der Umgebungsvariable `ODBCSYSINI` verwenden. Beispiel:

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

In diesem Fall können Sie dem `Trace=Yes` `[ODBC Driver 13 for SQL Server]` Abschnitt von `/home/myappuser/odbcinst.ini`hinzufügen.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Bestimmen, welche odbc.ini-Datei der Treiber verwendet

Die Linux-und macOS-ODBC-Treiber wissen `odbc.ini` nicht, welche verwendet wird, oder den Pfad `odbc.ini` zur Datei. Informationen dazu, welche `odbc.ini` Datei verwendet wird, sind jedoch über die unixodbc-Tools `odbc_config` und `odbcinst`sowie über die unixodbc Driver Manager-Dokumentation verfügbar.

Beispielsweise gibt der folgende Befehl (unter anderem) den Speicherort der `odbc.ini`-System- und Benutzerdateien aus, die jeweils die System- und Benutzer-DSNs enthalten:

```
$ odbcinst -j
unixODBC 2.3.1
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/odbcuser/.odbc.ini`
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```

In der [unixodbc-Dokumentation](http://www.unixodbc.org/doc/UserManual/) werden die Unterschiede zwischen Benutzer-und System-DSNs erläutert. Zusammenfassung:

- Benutzer-DSNs---diese DSNs sind, die nur für einen bestimmten Benutzer verfügbar sind. Benutzer können mithilfe von eine Verbindung herstellen, ihre eigenen Benutzer-DSNs hinzufügen, ändern und entfernen. Benutzer-DSNs werden in einer Datei im Basisverzeichnis des Benutzers oder in einem Unterverzeichnis gespeichert.

- System-DSNs---diese DSNs sind für jeden Benutzer im System verfügbar, um eine Verbindung herzustellen. Sie können jedoch nur von einem Systemadministrator hinzugefügt, geändert und entfernt werden. Wenn ein Benutzer über einen Benutzer-DSN mit dem gleichen Namen wie ein System-DSN verfügt, wird der Benutzer-DSN bei Verbindungen durch diesen Benutzer verwendet.

## <a name="see-also"></a>Weitere Informationen

- [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)
