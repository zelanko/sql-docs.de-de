---
title: Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS
description: In diesem Artikel wird SSIS (SQL Server Integration Services) für Linux-Computer beschrieben.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: e6230ee4efebc4b1af873a61e9f2ebfc191df171
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67943816"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird beschrieben, wie SSIS-Pakte (SQL Server Integration Services) unter Linux ausgeführt werden. Mit SSIS können komplexe Probleme bei der Datenintegration behoben werden, indem Daten aus mehreren Quellen und Formaten extrahiert, anschließend transformiert und bereinigt und schließlich in mehrere Ziele geladen werden. 

Unter Linux ausgeführte SSIS-Pakete können eine Verbindung mit Microsoft SQL Server herstellen, das lokal oder in der Cloud unter Windows, unter Linux oder in Docker ausgeführt wird. Sie können auch eine Verbindung mit Azure SQL-Datenbank, Azure SQL Data Warehouse, ODBC-Datenquellen, Flatfiles und anderen Datenquellen wie ADO.NET-Quellen, XML-Dateien und OData-Services herstellen.

Weitere Informationen zu den Funktionen von SSIS finden Sie unter [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie SSIS-Pakete auf einem Linux-Computer ausführen möchten, installieren Sie zunächst SQL Server Integration Services. SSIS ist in der Installation von SQL Server für Linux-Computer nicht enthalten. Die Installationsanweisungen finden Sie unter [Installieren von SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Ferner benötigen Sie einen Windows-Computer zum Erstellen und Verwalten von Paketen. Bei den Entwurfs- und Verwaltungstools von SSIS handelt es sich um Windows-Anwendungen, die derzeit für Linux-Computer noch nicht verfügbar sind. 

## <a name="run-an-ssis-package"></a>Ausführen eines SSIS-Pakets

Führen Sie zum Ausführen eines SSIS-Pakets folgende Schritte aus:

1.  Kopieren Sie das SSIS-Paket auf den Linux-Computer.
2.  Führen Sie den folgenden Befehl aus:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Ausführen eines verschlüsselten (kennwortgeschützten) Pakets
Es gibt drei Möglichkeiten, ein mit einem Kennwort verschlüsseltes SSIS-Pakte auszuführen:

1.  Legen Sie den Wert der Umgebungsvariablen `SSIS_PACKAGE_DECRYPT` wie im folgenden Beispiel darstellt fest:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Geben Sie die Option `/de[crypt]` wie im folgenden Beispiel dargestellt an, damit das Kennwort interaktiv eingegeben werden kann:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Geben Sie die Option `/de` wie im folgenden Beispiel dargestellt an, um das Kennwort in der Befehlszeile einzugeben. Diese Methode wird nicht empfohlen, da damit das Entschlüsselungskennwort mit dem Befehl im Befehlsverlauf gespeichert wird.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Entwerfen von Paketen

**Stellen Sie eine Verbindung mit ODBC-Datenquellen her**. Mit SSIS unter Linux CTP 2.1 Refresh und höher können SSIS-Pakete ODBC-Verbindungen unter Linux verwenden. Diese Funktion wurde mit den Treibern von SQL Server und MySQL ODBC getestet, sollte jedoch auch mit einem Unicode-Treiber verwendet werden können, der der ODBC-Spezifikation entspricht. Zur Entwurfszeit können Sie entweder einen DSN oder eine Verbindungszeichenfolge angeben, um eine Verbindung mit den ODBC-Daten herzustellen. Sie können aber auch die Windows-Authentifizierung verwenden. Weitere Informationen hierzu finden Sie im [Blogbeitrag mit der Ankündigung zur ODBC-Unterstützung unter Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Pfade**. Geben Sie in Ihren SSIS-Paketen Windows-Pfade an. SSIS unter Linux unterstützt keine Linux-Pfade, ordnet jedoch Windows-Pfade zur Laufzeit Linux-Pfaden zu. So ordnet SSIS unter Linux beispielsweise den Windows-Pfad `C:\test` dem Linux-Pfad `/test` zu.

## <a name="deploy-packages"></a>Bereitstellen von Paketen
Pakete können in diesem Release nur im Dateisystem unter Linux gespeichert werden. Die SSIS-Katalogdatenbank und der Legacy-SSIS-Service sind unter Linux nicht für die Paketbereitstellung und -speicherung verfügbar.

## <a name="schedule-packages"></a>Planen von Paketen
Zum Planen von Paketen können Sie Planungstools des Linux-Systems wie `cron` verwenden. SQL-Agent unter Linux können Sie in diesem Release dagegen nicht zum Planen der Paketausführung verwenden. Weitere Informationen finden Sie unter [Schedule SSIS packages on Linux with cron (Planen von SSIS-Paketen unter Linux mit Cron)](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

Ausführliche Informationen zu den Einschränkungen und bekannten Problemen bei SSIS unter Linux finden Sie unter [Limitations and known issues for SSIS on Linux (Einschränkungen und bekannte Probleme bei SSIS unter Linux)](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Weitere Informationen zu SSIS unter Linux

Weitere Informationen zu SSIS unter Linux finden Sie in den folgenden Blogbeiträgen:

-   [SSIS on Linux is available in SQL Server CTP 2.1 (SSIS unter Linux ist in SQL Server CTP 2.1 verfügbar)](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC is supported in SSIS on Linux (SQL Server CTP 2.1 refresh) (ODBC wird in SSIS unter Linux unterstützt (SQL Server CTP 2.1-Aktualisierung))](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Weitere Informationen zu SSIS

Microsoft SQL Server Integration Services (SSIS) ist eine Plattform zum Erstellen von leistungsstarken Datenintegrationslösungen, z. B. ETL-Paketen (Extrahieren, Transformieren und Laden) für das Data Warehousing. Weitere Informationen zu SSIS finden Sie unter [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS umfasst die folgenden Funktionen:
- Grafische Tools und Assistenten zum Entwickeln und Debuggen von Paketen unter Windows
- Eine Reihe von Aufgaben zum Ausführen von Workflow Funktionen wie FTP-Vorgänge, zum Ausführen von SQL-Anweisungen sowie zum Senden von E-Mail-Nachrichten
- Eine Reihe von Datenquellen und Zielen zum Extrahieren und Laden von Daten
- Eine Reihe von Transformationen zum Bereinigen, Aggregieren, Zusammenführen und Kopieren von Daten
- APIs (Application Programming Interfaces, Anwendungsprogrammierschnittstellen) zur Erweiterung von SSIS mit eigenen benutzerdefinierten Skripts und Komponenten

Laden Sie für den Einstieg in SSIS die neueste Version von [SSDT (SQL Server Data Tools)](../integration-services/ssis-how-to-create-an-etl-package.md) herunter.

Weitere Informationen zu SSIS erhalten Sie in den folgenden Artikeln:
- [SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) – Entwicklungs- und Verwaltungstools](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Integration Services-Tutorials](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Install SQL Server Integration Services (SSIS) on Linux (Installieren von SSIS (SQL Server Integration Services) unter Linux)](sql-server-linux-setup-ssis.md)
-   [Configure SQL Server Integration Services on Linux with ssis-conf (Konfigurieren von SQL Server Integration Services unter Linux mit ssis-conf)](sql-server-linux-configure-ssis.md)
-   [Limitations and known issues for SSIS on Linux (Einschränkungen und bekannte Probleme bei SSIS unter Linux)](sql-server-linux-ssis-known-issues.md)
-   [Schedule SQL Server Integration Services package execution on Linux with cron (Zeitliches Planen der Ausführung von SSIS-Paketen mit Cron)](sql-server-linux-schedule-ssis-packages.md)
