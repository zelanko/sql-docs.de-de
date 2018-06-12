---
title: Ausführen von SSIS-Paketen in Azure | Microsoft-Dokumentation
ms.description: Provides an overview of the available methods for running packages deployed to Azure SQL Database.
ms.date: 05/29/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e4d733b49f8353fc430f90161ef25c352c8cac8f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34586085"
---
# <a name="run-an-ssis-package-in-azure"></a>Ausführen eines SSIS-Pakets in Azure

Sie können die in der Datenbank des SSISDB-Katalogs bereitgestellten SSIS-Pakete auf einem Azure SQL-Datenbankserver ausführen, indem Sie eine der in diesem Artikel erläuterten Optionen auswählen. Sie können ein Paket direkt oder als Teil einer Azure Data Factory-Pipeline ausführen. Eine Übersicht über SSIS in Azure finden Sie unter [Migration von SQL Server Integration Services-Workloads in die Cloud per Lift und Shift](ssis-azure-lift-shift-ssis-packages-overview.md).

- Direktes Ausführen eines Pakets

  - [Ausführen mit SSMS](#ssms)

  - [Ausführen mit gespeicherten Prozeduren](#sproc)

  - [Ausführen mit Skript oder Code](#script)

- Ausführen eines Pakets als Teil einer Azure Data Factory-Pipeline

  - [Ausführen mit der Aktivität „SSIS-Paket ausführen“](#exec_activity)

  - [Ausführen mit der Aktivität „Gespeicherte Prozedur“](#sproc_activity)

> [!NOTE]
> Das Ausführen eines Pakets mit `dtexec.exe` wurde bei in Azure bereitgestellten Paketen nicht getestet.

## <a name="ssms"></a> Ausführen eines Pakets mit SSMS

In SQL Server Management Studio (SSMS) können Sie mit der rechten Maustaste auf ein Paket klicken, das in der SSIS-Katalogdatenbank SSISDB bereitgestellt wurde, und **Ausführen** auswählen, um das Dialogfeld **Paket ausführen** zu öffnen. Weitere Informationen finden Sie unter [Run an SSIS package with SQL Server Management Studio (SSMS) (Ausführen eines SSIS-Pakets mit SQL Server Management Studio (SSMS))](../ssis-quickstart-run-ssms.md).

## <a name="sproc"></a> Ausführen eines Pakets mit gespeicherten Prozeduren

Sie können in jeder Umgebung, in der Sie eine Verbindung mit Azure SQL-Datenbank herstellen und Transact-SQL-Code ausführen können, ein Paket ausführen, indem Sie folgende gespeicherte Prozeduren aufrufen:

1. **[catalog].[create_execution]**. Weitere Informationen finden Sie unter [catalog.create_execution](../system-stored-procedures/catalog-create-execution-ssisdb-database.md).

2. **[catalog].[set_execution_parameter_value]**. Weitere Informationen finden Sie unter [catalog.set_execution_parameter_value](../system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md).

3. **[catalog].[start_execution]** Weitere Informationen finden Sie unter [catalog.start_execution](../system-stored-procedures/catalog-start-execution-ssisdb-database.md).

Weitere Informationen finden Sie in den folgenden Beispielen:

- [Ausführen eines SSIS-Pakets aus SSMS mit Transact-SQL](../ssis-quickstart-run-tsql-ssms.md)

- [Ausführen eines SSIS-Pakets aus Visual Studio Code mit Transact-SQL](../ssis-quickstart-run-tsql-vscode.md)

## <a name="script"></a> Ausführen eines Pakets mit Skript oder Code

Sie können in jeder Entwicklungsumgebung, in der Sie eine verwaltete API aufrufen können, ein Paket ausführen, indem Sie die Methode `Execute` des Objekts `Package` im Namespace `Microsoft.SQLServer.Management.IntegrationServices` aufrufen.

Weitere Informationen finden Sie in den folgenden Beispielen:

- [Run an SSIS package with PowerShell](../ssis-quickstart-run-powershell.md) (Ausführen eines SSIS-Pakets mit PowerShell)

- [Ausführen eines SSIS-Pakets mit C#-Code in einer .NET-App](../ssis-quickstart-run-dotnet.md)

## <a name="exec_activity"></a> Ausführen eines Pakets mit der Aktivität „SSIS-Paket ausführen“

Weitere Informationen finden Sie unter [Ausführen eines SSIS-Pakets mit der Aktivität „SSIS-Paket ausführen“ in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="sproc_activity"></a> Ausführen eines Pakets mit der Aktivität „Gespeicherte Prozedur“

Weitere Informationen finden Sie unter [Ausführen eines SSIS-Pakets mit der Aktivität „Gespeicherte Prozedur“ in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity).

## <a name="next-steps"></a>Nächste Schritte

In diesem Abschnitt erhalten Sie Informationen zu Optionen für die Planung von in Azure bereitgestellten SSIS-Paketen. Weitere Informationen finden Sie unter [Planen der Ausführung eines SSIS-Pakets in Azure](ssis-azure-schedule-packages.md).