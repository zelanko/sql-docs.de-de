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
manager: craigg
ms.openlocfilehash: 0ad5d49841db9abdd0b512c1d36454eccc5ff73a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782878"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Ablaufverfolgung des Datenzugriffs mit dem ODBC-Treiber unter Linux und macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der UnixODBC-Treiber-Manager unter MacOS und Linux unterstützt die Ablaufverfolgung von ODBC-API-Aufruf-Eintrag, und Beenden des ODBC-Treibers für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Um das Verhalten Ihrer Anwendung ODBC zu verfolgen, bearbeiten Sie die `odbcinst.ini` Datei `[ODBC]` Abschnitt zum Festlegen der Werte `Trace=Yes` und `TraceFile` auf den Pfad der Datei, die in der Ablaufverfolgungsausgabe; enthalten z. B.:

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(Sie können auch `/dev/stdout` oder den Namen eines anderen Geräts Ablaufverfolgungsausgabe gibt es nicht in einer persistenten Datei senden.) Mit den obigen Einstellungen jedes Mal, wenn eine Anwendung den UnixODBC Treiber-Manager lädt werden sie alle ODBC-API-Aufrufe aufgezeichnet, den sie in die Ausgabedatei ausgeführt.

Entfernen Sie nach Abschluss der Ablaufverfolgung für Ihre Anwendung `Trace=Yes` aus der `odbcinst.ini` -Datei, um Leistungseinbußen während der Ablaufverfolgung zu vermeiden und sicherzustellen, dass unnötigen Ablaufverfolgungsdateien werden entfernt.
  
Die Ablaufverfolgung gilt für alle Anwendungen, die den Treiber in `odbcinst.ini` verwenden. Um nicht alle Anwendungen zu verfolgen (z.B., damit benutzerbezogene vertrauliche Informationen nicht weitergegeben werden), können Sie eine einzelne Anwendungsinstanz verfolgen, indem Sie den Speicherort einer privaten `odbcinst.ini`-Datei mit der Umgebungsvariable `ODBCSYSINI` verwenden. Zum Beispiel:  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
Sie können in diesem Fall hinzufügen `Trace=Yes` auf die `[ODBC Driver 13 for SQL Server]` Abschnitt `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Bestimmen, welche odbc.ini-Datei der Treiber verwendet

Die ODBC-Treiber für Linux und MacOS wissen nicht, die `odbc.ini` verwendet wird, oder der Pfad zu der `odbc.ini` Datei. Allerdings Informationen dazu, welche `odbc.ini` Datei befindet sich in Verwendung ist verfügbar, über die UnixODBC-Tools `odbc_config` und `odbcinst`, und von den UnixODBC Treiber-Manager-Dokumentation.  
  
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

Die [UnixODBC-Dokumentation](http://www.unixodbc.org/doc/UserManual/) erläutert den Unterschied zwischen Benutzer und System-DSNs. Zusammenfassung:  

- Benutzer-DSNs---Hierbei handelt es sich um DSNs, die nur für einen bestimmten Benutzer verfügbar sind. Benutzer können Herstellen einer Verbindung mit hinzufügen, ändern und eigene Benutzer-DSNs entfernen. Benutzer-DSNs werden in einer Datei im Basisverzeichnis des Benutzers oder davon ein Unterverzeichnis gespeichert.
  
- System-DSNs---diese DSNs stehen für alle Benutzer des Systems für die verbindungsherstellung, jedoch können nur hinzugefügt, geändert, und entfernt werden von einem Systemadministrator. Wenn ein Benutzer einen Benutzer-DSN mit dem gleichen Namen wie ein System-DSN hat, wird der Benutzer-DSN nach Verbindungen von diesem Benutzer verwendet werden.

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)
