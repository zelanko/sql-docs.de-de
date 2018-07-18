---
title: Installieren und konfigurieren Sie die Beispieldatenbank "WideWorldImporters"-SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d1d00b5d3e5650e628935c840f280b278869b62
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984842"
---
# <a name="installation-and-configuration"></a>Installation und Konfiguration
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Wide World Importers-OLTP-Datenbank Installations- und konfigurationsanweisungen.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQL Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) (oder höher) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie für die vollständige Version des Beispiels SQL Server-Evaluierung, Developer, Enterprise Edition ein.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie das Release vom Juni 2016 oder höher.

## <a name="download"></a>Herunterladen

Die neueste Version des Beispiels:

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

Herunterladen Sie die Beispiel "wideworldimporters" Datenbank sichern/bacpac-Datei, die entspricht Ihrer Version von SQL Server oder Azure SQL-Datenbank.

Quellcode die-Beispieldatenbank neu zu erstellen ist aus folgendem Ort verfügbar. Beachten Sie, dass das Neuerstellen des Beispiels führt in geringfügige Unterschiede in den Daten, da ein Zufallsfaktor in die datengenerierung vorhanden ist:

[Wide-Welt-Importer](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

## <a name="install"></a>Install


### <a name="sql-server"></a>SQL Server

Um eine Sicherung einer SQL Server-Instanz wiederherzustellen, können Sie Management Studio verwenden.

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit der SQL Server-Zielinstanz.
2. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Restore Database**.
3. Wählen Sie **Gerät** und klicken Sie auf die Schaltfläche mit den **...**
4. Im Dialogfeld **Sicherungsmedien auswählen**, klicken Sie auf **hinzufügen**, navigieren Sie zu der datenbanksicherung in das Dateisystem des Servers ein, und wählen Sie die Sicherung. Klicken Sie auf **OK**.
5. Bei Bedarf ändern, das der Zielort für die Daten und Protokolldateien, in der **Dateien** Bereich. Beachten Sie, dass es wird empfohlen, zum Hinzufügen von Daten und Protokolldateien auf verschiedenen Laufwerken.
6. Klicken Sie auf **OK**. Dadurch wird die Wiederherstellung der Datenbank ausgelöst. Nachdem der Vorgang abgeschlossen ist, müssen Sie die Datenbank "wideworldimporters" auf Ihrer SQL Server-Instanz installiert.

### <a name="azure-sql-database"></a>Azure SQL-Datenbank

Zum Importieren einer bacpac-Datei in eine neue SQL-Datenbank können Sie Management Studio verwenden.

1. (optional) Wenn Sie noch keinem SQL Server in Azure verfügen, navigieren Sie zu der [Azure-Portal](https://portal.azure.com/) , und erstellen Sie eine neue SQL-Datenbank. Dabei wird eine Datenbank erstellen, erstellen Sie einen Server. Notieren Sie den Server.
   - Finden Sie unter [in diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) zum Erstellen einer Datenbank in wenigen Minuten
2. Öffnen Sie SQL Server Management Studio, und Verbinden mit Ihrem Server in Azure.
3. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Import Data-Tier Application**.
4. In der **Importeinstellungen** wählen **vom lokalen Datenträger importieren** , und wählen Sie die bacpac-Datei der Beispieldatenbank aus Ihrem Dateisystem.
5. Klicken Sie unter **Datenbankeinstellungen** ändern Sie den Datenbanknamen an *"wideworldimporters"* , und wählen Sie die Ziel-Edition und das dienstziel verwenden.
6. Klicken Sie auf **Weiter** und **Fertig stellen** um die Bereitstellung zu starten. Es wird einige Minuten, um eine P1 abzuschließen. Wenn es sich bei einem niedrigeren Tarif Tarif gewünscht wird, es wird empfohlen, in eine neue P1-Datenbank importieren, und ändern Sie den Tarif auf die gewünschte Ebene.

## <a name="configuration"></a>Konfiguration

### <a name="full-text-indexing"></a>Volltextindizierung

Verwenden des Volltextindizierungs-ist die-Beispieldatenbank möglich. Allerdings das Feature wird nicht standardmäßig installiert, mit SQL Server – müssen Sie es während des Setups von SQL Server auswählen (ist standardmäßig in Azure SQL-Datenbank aktiviert). Aus diesem Grund ist ein Schritt nach der Installation erforderlich.

1. Klicken Sie im SQL Server Management Studio Verbinden mit der Datenbank "wideworldimporters", und öffnen Sie ein neues Abfragefenster.
2. Führen Sie den folgenden T-SQL-Befehl, um die Verwendung der Volltextindex in der Datenbank zu aktivieren:  `EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

Gilt für: SQLServer

Aktivieren der Überwachung in SQL Server ist eine Serverkonfiguration erforderlich. Um SQL Server-Überwachung für das Beispiel "wideworldimporters" zu aktivieren, führen Sie die folgende Anweisung in der Datenbank aus:

    EXECUTE [Application].[Configuration_ApplyAuditing]

In Azure SQL-Datenbank-Überwachung wird konfiguriert, über die [Azure-Portal](https://portal.azure.com/).

### <a name="row-level-security"></a>Sicherheit auf Zeilenebene

Gilt für: Azure SQL-Datenbank

Sicherheit auf Zeilenebene ist standardmäßig in der bacpac-Datei-Download von "wideworldimporters" nicht aktiviert. Um die Sicherheit auf Zeilenebene in der Datenbank zu aktivieren, führen Sie die folgende gespeicherte Prozedur aus:

    EXECUTE [Application].[Configuration_ApplyAuditing]

