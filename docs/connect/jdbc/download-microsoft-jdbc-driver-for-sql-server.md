---
title: Herunterladen des Microsoft JDBC-Treibers für SQL Server
description: Laden Sie den Microsoft JDBC-Treiber für SQL Server herunter, um Java-Anwendungen zu entwickeln, die eine Verbindung mit SQL Server und Azure SQL-Datenbank herstellen.
ms.date: 03/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ab209588a1bf05380ed1856ddfb90683e3259b3
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487184"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Herunterladen des Microsoft JDBC-Treibers für SQL Server

Der Microsoft JDBC-Treiber für SQL Server ist ein JDBC-Treiber vom Typ 4, der Datenbankkonnektivität über die JDBC-Standard-APIs (Anwendungsprogrammierschnittstellen) bereitstellt, die auf der Java-Plattform verfügbar sind. Der Treiber kann von allen Benutzern kostenlos heruntergeladen werden. Er ermöglicht den Zugriff auf SQL Server über alle Java-Anwendungen, Anwendungsserver oder Java-fähigen Apps.

## <a name="download"></a>Download

Die Version 8.2 ist die neueste allgemein verfügbare Version. Sie unterstützt Java 8, 11 und 13. Wenn Sie eine ältere Java-Runtime verwenden müssen, können Sie unter [Matrix zu unterstützten Java- und JDBC-Spezifikationen](microsoft-jdbc-driver-for-sql-server-support-matrix.md#java-and-jdbc-specification-support) überprüfen, ob es eine unterstützte Treiberversion gibt, die Sie verwenden können. Wir arbeiten stetig daran, die Unterstützung der Java-Konnektivität zu verbessern. Daher raten wir dringend zur Verwendung der neuesten Version des Microsoft JDBC-Treibers.

**[![Download](../../ssms/media/download-icon.png) Herunterladen des Microsoft JDBC-Treibers 8.2 für SQL Server (zip)](https://go.microsoft.com/fwlink/?linkid=2122433)**  
**[![Download](../../ssms/media/download-icon.png) Download des Microsoft JDBC-Treibers 8.2 für SQL Server (tar.gz)](https://go.microsoft.com/fwlink/?linkid=2122536)**  

### <a name="version-information"></a>Versionsinformationen

- Releasenummer: 8.2.2
- Veröffentlichung: 24. März 2020

Beim Herunterladen des Treibers gibt es mehrere JAR-Dateien. Der Name der JAR-Datei gibt die unterstützte Version von Java an.

> [!Note]
> Wenn Sie von einer nicht englischsprachigen Version auf diese Seite zugreifen und den neuesten Inhalt anzeigen möchten, besuchen Sie die [US-englische Version der Website](https://aka.ms/downloadmssqljdbcenglish). Sie können verschiedene Sprachen von der US-englischen Website herunterladen, indem Sie [available languages](#available-languages) (verfügbare Sprachen) auswählen.

## <a name="available-languages"></a>Verfügbare Sprachen

Dieses Release des Microsoft JDBC-Treibers für SQL Server ist in folgenden Sprachen verfügbar:

Microsoft JDBC-Treiber 8.2.2 für SQL Server (zip): [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x40a)

Microsoft JDBC-Treiber 8.2.2 für SQL Server (tar.gz): [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x40a)

### <a name="release-notes"></a>Versionshinweise

Ausführliche Informationen zu diesem Release finden Sie in den [Versionshinweisen](release-notes-for-the-jdbc-driver.md) und den [Systemanforderungen](system-requirements-for-the-jdbc-driver.md).

### <a name="previous-releases"></a>Vorgängerversionen

Downloads der vorherigen Releases finden Sie unter [Vorherige Releases des Microsoft JDBC-Treibers für SQL Server](release-notes-for-the-jdbc-driver.md#previous-releases).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Verwenden des JDBC-Treibers mit Maven Central

Der JDBC-Treiber kann einem Maven-Projekt hinzugefügt werden, indem Sie ihn in der Datei „POM.xml“ mit dem folgenden Code als Abhängigkeit hinzufügen:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.2.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Nicht unterstützte Treiber

Nicht unterstützte Treiber werden hier nicht zum Download angeboten. Wir arbeiten laufend daran, die Unterstützung der Java-Konnektivität zu verbessern. Daher raten wir dringend zur Verwendung der neuesten Version des Microsoft JDBC-Treibers.  
  
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Microsoft JDBC-Treiber für SQL Server finden Sie unter [Übersicht über den JDBC-Treiber](overview-of-the-jdbc-driver.md) und im [GitHub-Repository für den JDBC-Treiber](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
