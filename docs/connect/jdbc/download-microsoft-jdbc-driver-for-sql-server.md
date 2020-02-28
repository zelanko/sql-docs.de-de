---
title: Herunterladen des Microsoft JDBC-Treibers für SQL Server
description: Laden Sie den Microsoft JDBC-Treiber für SQL Server herunter, um Java-Anwendungen zu entwickeln, die eine Verbindung mit SQL Server herstellen.
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fcf034b332494750885d4808b54c9cb62c37077c
ms.sourcegitcommit: 4b2c9d648b7a7bdf9c3052ebfeef182e2f9d66af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "77013115"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Herunterladen des Microsoft JDBC-Treibers für SQL Server

In diesem Artikel finden Sie Downloadlinks für den Microsoft JDBC-Treiber für SQL Server. Mit diesem Treiber können Sie Java-Anwendungen entwickeln, die eine Verbindung mit SQL Server herstellen können.  

## <a name="available-downloads-of-jdbc-driver-for-sql-server"></a>Verfügbare Downloads des JDBC-Treibers für SQL Server

Verwenden Sie die Links in der folgenden Tabelle, um den neuesten JDBC-Treiber für SQL Server herunterzuladen, der mit Ihrer Java Runtime Environment übereinstimmt:

| Version | Veröffentlichungsdatum | Java-Versionen |
|---|---|---|
| [Microsoft JDBC-Treiber 8.2](https://go.microsoft.com/fwlink/?linkid=2116870) | 31.01.2020 | JRE 8, 11, 13 |
| [Microsoft JDBC-Treiber 7.4](https://go.microsoft.com/fwlink/?linkid=2099962) | 01.08.2019 | JRE 8, 11, 12 |
| [Microsoft JDBC-Treiber 7.2](https://go.microsoft.com/fwlink/?linkid=2063159) | 17.04.2019 | JRE 8, 11 |
| [Microsoft JDBC-Treiber 7.0](https://go.microsoft.com/fwlink/?linkid=2005972) | 31.07.2018 | JRE 8, 10 |
| [Microsoft JDBC-Treiber 6.4](https://go.microsoft.com/fwlink/?linkid=868290)  | 26.03.2018 | JRE 7, 8, 9 |
| [Microsoft JDBC-Treiber 6.2](https://go.microsoft.com/fwlink/?linkid=852460) | 12.02.2018 | JRE 7, 8 |
| [Microsoft JDBC-Treiber 6.0](https://go.microsoft.com/fwlink/?LinkId=245496) | 27.02.2018 | JRE 7, 8 |
| [Microsoft JDBC-Treiber 4.2](https://go.microsoft.com/fwlink/?linkid=841534) | 26.02.2018 | JRE 7, 8 |

Beim Herunterladen des Treibers gibt es mehrere JAR-Dateien. Der Name der JAR-Datei gibt die unterstützte Version von Java an. Weitere Informationen zu den einzelnen Releases finden Sie in den [Versionshinweisen](release-notes-for-the-jdbc-driver.md) und in den [Systemanforderungen](system-requirements-for-the-jdbc-driver.md).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Verwenden des JDBC-Treibers mit Maven Central

Der JDBC-Treiber kann einem Maven-Projekt hinzugefügt werden, indem Sie ihn in der Datei „POM.xml“ mit dem folgenden Code als Abhängigkeit hinzufügen:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.0.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Nicht unterstützte Treiber

Nicht unterstützte Treiber werden hier nicht zum Download angeboten. Wir arbeiten laufend daran, die Unterstützung der Java-Konnektivität zu verbessern. Daher raten wir dringend zur Verwendung der neuesten Version des Microsoft JDBC-Treibers.  
  
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Microsoft JDBC-Treiber für SQL Server finden Sie unter [Übersicht über den JDBC-Treiber](overview-of-the-jdbc-driver.md) und im [GitHub-Repository für den JDBC-Treiber](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
