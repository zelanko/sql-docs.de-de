---
title: Ändern des Kontos für die Scale Out-Protokollierung | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie das Benutzerkonto für die SSIS Scale Out-Protokollierung ändern.
ms.custom: performance
ms.date: 06/29/2020
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.reviewer: maghan
ms.openlocfilehash: 0478b685adffa36b4ec344f4f13c52da6436300c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919036"
---
# <a name="change-the-account-for-scale-out-logging"></a>Ändern des Kontos für die Scale Out-Protokollierung

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Beim Ausführen von SSIS-Paketen in Scale Out werden die Ereignismeldungen mit einem automatisch erstellten Benutzerkonto mit dem Namen **##MS_SSISLogDBWorkerAgentLogin##** in der SSISDB-Datenbank protokolliert. Bei der Anmeldung dieses Benutzers wird die SQL Server-Authentifizierung verwendet.

Führen Sie die folgenden Schritte aus, wenn Sie das für die Scale Out-Anmeldung verwendete Konto ändern möchten:

> [!NOTE]
> Wenn Sie ein Windows-Benutzerkonto für die Protokollierung verwenden, nutzen Sie das Konto, das den Scale Out-Workerdienst ausführt. Andernfalls tritt bei der Anmeldung bei SQL Server ein Fehler auf.

## <a name="1-create-a-user-for-ssisdb"></a>1. Erstellen Sie einen SSISDB-Benutzer
Anweisungen zum Erstellen eines Datenbankbenutzers finden Sie unter [Erstellen eines Datenbankbenutzers](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-the-database-role-ssis_cluster_worker"></a>2. Fügen Sie den Benutzer zur Datenbankrolle „ssis_cluster_worker“ hinzu

Anweisungen zum Verknüpfen einer Datenbankrolle finden Sie unter [Verknüpfen einer Rolle](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-the-logging-information-in-ssisdb"></a>3. Aktualisieren Sie die Protokollierungsinformationen in SSISDB
Rufen Sie die gespeicherte Prozedur `[catalog].[update_logdb_info]` mit dem SQL Server-Namen und der Verbindungszeichenfolge als Parameter auf. Dies wird in folgendem Beispiel veranschaulicht:

```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-the-scale-out-worker-service"></a>4. Starten Sie den Scale Out-Workerdienst neu
Starten Sie den Scale Out-Workerdienst neu, damit die Änderungen wirksam werden.

## <a name="next-steps"></a>Nächste Schritte
-   [Integration Services Scale Out-Manager](integration-services-ssis-scale-out-manager.md)
