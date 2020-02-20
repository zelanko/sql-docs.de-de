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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68008819"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Datenzugriffs-Ablaufverfolgung mit dem ODBC-Treiber unter Linux und macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der unixODBC-Treibermanager unter macOS und Linux unterstützt die Nachverfolgung von ODBC-API-Aufrufeinträgen und das Beenden des ODBC-Treibers für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Um das ODBC-Verhalten Ihrer Anwendung nachzuverfolgen, bearbeiten Sie den `[ODBC]`-Abschnitt der Datei `odbcinst.ini`, und legen Sie die Werte `Trace=Yes` und `TraceFile` auf den Pfad der Datei fest, in der die Ablaufverfolgungsausgabe enthalten sein soll. Beispiel:

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Anstelle einer persistenten Datei können Sie auch `/dev/stdout` oder den Namen eines beliebigen anderen Geräts verwenden, an das die Ablaufverfolgungsausgabe gesendet werden soll.) Mit den oben genannten Einstellungen zeichnet eine Anwendung bei jedem Laden des unixODBC-Treiber-Managers alle ausgeführten ODBC-API-Aufrufe in der Ausgabedatei auf.

Wenn Sie die Ablaufverfolgung Ihrer Anwendung abgeschlossen haben, entfernen Sie `Trace=Yes` aus der Datei `odbcinst.ini`, um Leistungseinbußen durch die Ablaufverfolgung zu vermeiden, und stellen Sie sicher, dass alle Ablaufverfolgungsdateien entfernt wurden.

Die Ablaufverfolgung gilt für alle Anwendungen, die den Treiber in `odbcinst.ini` verwenden. Um nicht alle Anwendungen zu verfolgen (z.B., damit benutzerbezogene vertrauliche Informationen nicht weitergegeben werden), können Sie eine einzelne Anwendungsinstanz verfolgen, indem Sie den Speicherort einer privaten `odbcinst.ini`-Datei mit der Umgebungsvariable `ODBCSYSINI` verwenden. Beispiel:

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

In diesem Fall können Sie `Trace=Yes` zum `[ODBC Driver 13 for SQL Server]`-Abschnitt von `/home/myappuser/odbcinst.ini` hinzufügen.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Bestimmen, welche odbc.ini-Datei der Treiber verwendet

Die Linux- und macOS-ODBC-Treiber wissen nicht, welche `odbc.ini`-Datei verwendet wird, und kennen den Pfad zur `odbc.ini`-Datei nicht. Informationen darüber, welche `odbc.ini`-Datei verwendet wird, sind jedoch über die unixODBC-Tools `odbc_config` und `odbcinst` und in der Dokumentation des unixODBC-Treiber-Managers verfügbar.

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

In der [unixODBC-Dokumentation](http://www.unixodbc.org/doc/UserManual/) werden die Unterschiede zwischen Benutzer- und System-DSN erläutert. Zusammenfassung:

- Benutzer-DSNs: Dies sind die DSNs, die nur für einen bestimmten Benutzer verfügbar sind. Benutzer können über ihren eigenen Benutzer-DSN eine Verbindung erstellen und diesen hinzufügen, ändern und entfernen. Benutzer-DSNs werden in einer Datei im Basisverzeichnis eines Benutzers oder einem zugehörigen Unterverzeichnis gespeichert.

- System-DSNs: Diese DSNs stehen allen Benutzern im System zum Herstellen einer Verbindung zur Verfügung, können aber nur durch einen Systemadministrator hinzugefügt, geändert und entfernt werden. Wenn ein Benutzer über einen Benutzer-DSN verfügt, der genauso lautet wie ein System-DSN, wird der Benutzer-DSN für durch diesen Benutzer hergestellte Verbindungen verwendet.

## <a name="see-also"></a>Weitere Informationen

- [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)
