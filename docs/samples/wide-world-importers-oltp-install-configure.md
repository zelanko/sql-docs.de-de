---
title: Installieren und Konfigurieren der WideWorldImporters-Beispieldatenbank
description: Befolgen Sie diese Anweisungen zum Herunterladen, Installieren und Konfigurieren der WideWorldImporters-Beispieldatenbank mit SQL Server Management Studio.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 355eaa254fcc7bb6cd4aa9a39c2cbcb269d88396
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487069"
---
# <a name="installation-and-configuration"></a>Installation und Konfiguration
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Wide World Importers OLTP-Datenbankinstallations- und -konfigurationsanweisungen.

## <a name="prerequisites"></a>Voraussetzungen

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (oder höher) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie für die Vollversion des Beispiels SQL Server Evaluation/Developer/Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie die Version Juni 2016 oder höher.

## <a name="download"></a>Download

Die neueste Version des Beispiels:

[Weit-Welt-Importeur-Release](https://go.microsoft.com/fwlink/?LinkID=800630)

Laden Sie das Beispiel WideWorldImporters-Datenbanksicherung/-bacpac herunter, das Ihrer Edition von SQL Server oder Azure SQL Database entspricht.

Der Quellcode zum Neuerstellen der Beispieldatenbank ist am folgenden Speicherort verfügbar. Beachten Sie, dass das Erneute Erstellen der Stichprobe zu geringfügigen Unterschieden in den Daten führt, da es einen Zufallsfaktor in der Datengenerierung gibt:

[Weitwelt-Importeure](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>Installieren


### <a name="sql-server"></a>SQL Server

Um eine Sicherung auf einer SQL Server-Instanz wiederherzustellen, können Sie Management Studio verwenden.

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Datenbank wiederherstellen**aus.
3. Wählen Sie **Gerät** und klicken Sie auf die Schaltfläche **...**
4. Klicken Sie im Dialogfeld **Sicherungsgeräte auswählen**auf **Hinzufügen**, navigieren Sie zur Datenbanksicherung im Dateisystem des Servers, und wählen Sie die Sicherung aus. Klicken Sie auf **OK**.
5. Ändern Sie bei Bedarf den Zielspeicherort für die Daten- und Protokolldateien im Bereich **Dateien.** Beachten Sie, dass es am besten ist, Daten und Protokolldateien auf verschiedenen Laufwerken zu platzieren.
6. Klicken Sie auf **OK**. Dadurch wird die Datenbankwiederherstellung initiiert. Nach Abschluss der Datei ist die Datenbank WideWorldImporters auf Ihrer SQL Server-Instance installiert.

### <a name="azure-sql-database"></a>Azure SQL-Datenbank

Um ein Bacpac in eine neue SQL-Datenbank zu importieren, können Sie Management Studio verwenden.

1. (optional) Wenn Sie noch nicht über einen SQL Server in Azure verfügen, navigieren Sie zum [Azure-Portal,](https://portal.azure.com/) und erstellen Sie eine neue SQL-Datenbank. Beim Erstellen einer Datenbank erstellen Sie einen Server. Notieren Sie sich den Server.
   - In [diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) zum Erstellen einer Datenbank in wenigen Minuten
2. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit Ihrem Server in Azure her.
3. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Datentier-Anwendung importieren**aus.
4. Wählen Sie in den **Importeinstellungen** **Import von einem lokalen Datenträger** aus und wählen Sie das Bacpac der Beispieldatenbank aus Ihrem Dateisystem aus.
5. Ändern Sie unter **Datenbankeinstellungen** den Datenbanknamen in *WideWorldImporters,* und wählen Sie die zu verwendende Zieledition und das Dienstziel aus.
6. Klicken Sie auf **Weiter** und **Beenden,** um die Bereitstellung zu starten. Es wird ein paar Minuten auf einem P1 abzuschließen. Wenn eine niedrigere Preisstufe gewünscht wird, wird empfohlen, in eine neue P1-Datenbank zu importieren und dann die Preisstufe auf das gewünschte Niveau zu ändern.

## <a name="configuration"></a>Konfiguration

### <a name="full-text-indexing"></a>Volltextindizierung

Die Beispieldatenbank kann die Volltextindizierung verwenden. Dieses Feature ist jedoch nicht standardmäßig mit SQL Server installiert – Sie müssen es während der EINRICHTUNG von SQL Server auswählen (es ist standardmäßig in Azure SQL DB aktiviert). Daher ist ein Schritt nach der Installation erforderlich.

1. Stellen Sie in SQL Server Management Studio eine Verbindung mit der WideWorldImporters-Datenbank her, und öffnen Sie ein neues Abfragefenster.
2. Führen Sie den folgenden T-SQL-Befehl aus, um die Verwendung der Volltextindizierung in der Datenbank zu aktivieren:`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

Gilt für: SQL Server

Das Aktivieren der Überwachung in SQL Server erfordert eine Serverkonfiguration. Um die SQL Server-Überwachung für das WideWorldImporters-Beispiel zu aktivieren, führen Sie die folgende Anweisung in der Datenbank aus:

    EXECUTE [Application].[Configuration_ApplyAuditing]

In Azure SQL-Datenbank wird Audit über das [Azure-Portal](https://portal.azure.com/)konfiguriert.

### <a name="row-level-security"></a>Sicherheit auf Zeilenebene

Gilt für: Azure SQL-Datenbank

Die Row-Level-Sicherheit ist standardmäßig nicht im Bacpac-Download von WideWorldImporters aktiviert. Führen Sie die folgende gespeicherte Prozedur aus, um die Row-Level-Sicherheit in der Datenbank zu aktivieren:

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

