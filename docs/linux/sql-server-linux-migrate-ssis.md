---
title: Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die SQL Server Integration Services (SSIS) für Linux-Computer
author: lrtoyou1223
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 9790835dfa3f81105ac36818ecdda418c5433a84
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488355"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt, wie SQL Server Integration Services (SSIS)-Pakete unter Linux ausgeführt wird. SSIS löst Probleme bei der Integration von komplexen Daten extrahieren von Daten aus mehreren Quellen und Formaten, Transformieren und Bereinigen der Daten und die Daten in mehrere Ziele laden. 

SSIS-Pakete, die unter Linux können mit Microsoft SQL Server unter Windows lokal oder in der Cloud, die auf Linux oder in Docker verbinden. Sie können auch mit Azure SQL-Datenbank, Azure SQL Data Warehouse, ODBC-Datenquellen, Flatfiles und anderen Datenquellen, einschließlich ADO.NET Quellen, XML-Dateien und OData-Diensten verbinden.

Weitere Informationen zu den Funktionen von SSIS finden Sie unter [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Um die SSIS-Pakete auf einem Linux-Computer ausführen zu können, müssen Sie zuerst installieren Sie SQL Server Integration Services. SSIS ist nicht bei der Installation von SQL Server für Linux-Computer enthalten. Installationsanweisungen finden Sie unter [Installieren von SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Sie haben auch, dass ein Windows-Computer erstellen und Verwalten von Paketen. Die SSIS-Entwurfs- und -Tools sind Windows-Anwendungen, die derzeit nicht verfügbar für Linux-Computer sind. 

## <a name="run-an-ssis-package"></a>Ausführen eines SSIS-Pakets

Führen Sie zum Ausführen eines SSIS-Pakets auf einem Linux-Computer die folgenden Schritte aus:

1.  Kopieren Sie das SSIS-Paket auf den Linux-Computer.
2.  Führen Sie den folgenden Befehl aus:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Führen Sie ein verschlüsseltes Paket mit (ein Kennwort geschützt)
Es gibt drei Möglichkeiten zum Ausführen eines SSIS-Pakets, das verschlüsselt werden mit einem Kennwort:

1.  Legen Sie den Wert der Umgebungsvariablen `SSIS_PACKAGE_DECRYPT`, wie im folgenden Beispiel gezeigt:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Geben Sie die `/de[crypt]` Option, um das Kennwort einzugeben, interaktiv, wie im folgenden Beispiel gezeigt:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Geben Sie die `/de` Option aus, um das Kennwort in der Befehlszeile angeben, wie im folgenden Beispiel gezeigt. Diese Methode wird nicht empfohlen, da sie das Kennwort für die Entschlüsselung mit dem Befehl im Befehlsverlauf speichert.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Entwerfen von Paketen

**Herstellen einer Verbindung die ODBC-Datenquellen mit**. Mit SSIS unter Linux CTP 2.1 aktualisieren und höher können SSIS-Pakete auf Linux ODBC-Verbindungen. Diese Funktion wurde mit der SQL Server und MySQL-ODBC-Treiber getestet, aber es wird außerdem erwartet, dass alle Unicode-ODBC-Treiber zu arbeiten, die die ODBC-Spezifikation beobachtet. Zur Entwurfszeit können Sie einen DSN oder einer Verbindungszeichenfolge in die ODBC-Verbindung angeben; Sie können auch Windows-Authentifizierung verwenden. Weitere Informationen finden Sie in der [Blogbeitrag Ankündigung ODBC-Unterstützung für Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Pfade**. Geben Sie die Windows-Stil-Pfade in Ihrer SSIS-Paketen. SSIS unter Linux unterstützt keine Pfade für Linux-Format, aber Windows-Stil Pfade Linux-Stil Pfade zur Laufzeit zugeordnet. Klicken Sie dann ein, z. B. SSIS unter Linux ordnet den Windows-Stil Pfad `C:\test` auf den Pfad für die Linux-Stil `/test`.

## <a name="deploy-packages"></a>Bereitstellen von Paketen
Sie können nur Pakete im Dateisystem unter Linux in dieser Version speichern. SSIS-Katalogdatenbank und der legacy-SSIS-Dienst sind nicht für die Bereitstellung von Paketen und Storage unter Linux verfügbar.

## <a name="schedule-packages"></a>Planen von Paketen
Können Sie Linux-System Planungstools wie z. B. `cron` um Pakete zu planen. Sie können keine SQL-Agent unter Linux verwenden, zum Planen der Ausführung des Pakets in dieser Version. Weitere Informationen finden Sie unter [Zeitplan SSIS-Pakete für Linux mit Cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

Ausführliche Informationen zu den Einschränkungen und bekannte Probleme von SSIS unter Linux finden Sie unter [Einschränkungen und bekannte Probleme für SSIS für Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Weitere Informationen zu SSIS unter Linux

Weitere Informationen zu SSIS unter Linux finden Sie in den folgenden Blogbeiträgen:

-   [SSIS unter Linux finden Sie in SQL Server CTP2. 1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC ist in SSIS für Linux (Aktualisieren Sie SQL Server CTP 2.1) unterstützt.](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Weitere Informationen zu SSIS

Microsoft SQL Server Integration Services (SSIS) ist eine Plattform zum Erstellen von Hochleistungs-datenintegrationslösungen, z.B. extrahieren, Transformieren und laden (ETL) von Paketen für Data Warehouses. Weitere Informationen zu SSIS finden Sie unter [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS enthält die folgenden Features:
- Grafische Tools und Assistenten zum Erstellen und Debuggen von Paketen für Windows
- Eine Vielzahl von Aufgaben zum Ausführen von Workflowfunktionen wie z. B. FTP-Vorgänge, SQL-Anweisungen ausgeführt und Senden von e-Mail-Nachrichten
- Eine Vielzahl von Datenquellen und Ziele zum Extrahieren und Laden von Daten
- Eine Reihe von Transformationen für bereinigen, aggregieren, Zusammenführen und Kopieren von Daten
- Anwendungsprogrammierschnittstellen (APIs) zum Erweitern von SSIS mit Ihren eigenen benutzerdefinierten Skripts und Komponenten

Laden Sie die neueste Version von herunter, um den ersten Schritten mit SSIS [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Weitere Informationen zu SSIS finden Sie unter den folgenden Artikeln:
- [Erfahren Sie mehr über SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) Entwicklungs- und Verwaltungstools](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [SQL Serverintegration Services-Lernprogramme](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-conf](sql-server-linux-configure-ssis.md)
-   [Einschränkungen und bekannte Probleme für SSIS unter Linux](sql-server-linux-ssis-known-issues.md)
-   [Zeitplan SQL Server Integration Services-paketausführung unter Linux mit cron](sql-server-linux-schedule-ssis-packages.md)
