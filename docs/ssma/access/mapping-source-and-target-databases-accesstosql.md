---
title: Zuordnen von Quell- und Zieldatenbanken (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: acb6a8c71c3f144850cb9c24431bcff440cdf761
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395704"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Zuordnen von Quell- und Zieldatenbanken (AccessToSQL)
Wenn Sie eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, müssen Sie eine Zieldatenbank für die Migration angeben. Wenn Sie mehrere Access-Datenbanken haben können Sie sie mit mehreren zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken (oder Schemata) oder auf mehrere Schemas in die verbundene SQL Azure-Datenbank.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQLServer oder SQL Azure-Datenbankschemas  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken verwenden das Konzept von Schemas, um Objekte in einer Datenbank in logische Gruppen zu unterteilen. Beispielsweise können Bibliotheksdatenbank drei Schemas, die mit dem Namen **Bücher**, **audio**, und **video** , Audio- und Videodateien Buchobjekte voneinander zu trennen. In der Standardeinstellung die Access-Datenbank zugeordnet ist **master** Datenbank und **Dbo** Schema im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und verbundene Datenbank und **Dbo** -Schema in SQL Azure.  
  
Wenn Sie die Zuordnung zwischen einzelnen Access-Datenbank anpassen und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank und Schema SSMA werden migriert, die Schemas und Daten im Zusammenhang mit der Zugriffsdatenbank auf die Standarddatenbank zugeordnet.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und Schema  
SSMA können Sie jede zu Access-Datenbank zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank und Schema. Das folgende Verfahren beschreibt die zum Anpassen der Zuordnung pro Datenbank.  
  
**So ändern Sie die Zieldatenbank und das schema**  
  
1.  Wählen Sie im Bereich Metadaten-Explorer für den Zugriff **Metadaten zugreifen**.  
  
    Schemazuordnung ist auch verfügbar, bei der Auswahl der **Datenbanken** Knoten oder Knoten in der Datenbank. Die Liste der Schema-Zuordnung wird für das ausgewählte Objekt angepasst.  
  
2.  Klicken Sie im rechten Bereich auf die **Zuordnen von Schemas** Registerkarte.  
  
    Sehen Sie eine Tabelle mit Access Datenbanknamen und der entsprechenden SsNoVersion oder des Sql Azure-Schemas. Das Zielschema ist in einer zweiteiligen-Schreibweise (database.schema) gekennzeichnet.  
  
3.  Wählen Sie die Zeile, die die Zuordnung Sie anpassen möchten enthält, und klicken Sie dann auf **ändern**.  
  
4.  In der **Zielschema auswählen** im Dialogfeld können Sie für die Zieldatenbank verfügbar und Schema oder mit der Datenbank und des Schemas in das Textfeld in einer zweiteiligen-Schreibweise (database.schema) Namen, und klicken Sie dann auf Durchsuchen **OK**.  
  
**Modi der Zuordnung**  
  
-   Zuordnung zu SQLServer  
  
Sie können die Quelldatenbank zu keiner Zieldatenbank zuordnen. Standardmäßig wird die Quelldatenbank zugeordnet Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Sie verbunden haben, mit der SSMA. Wenn die Zieldatenbank, die zugeordnet wird, auf nicht vorhanden ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann mit einer Meldung werden Sie aufgefordert **"die Datenbank bzw. das Schema ist nicht im Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen?"** Klicken Sie auf "Ja". Auf ähnliche Weise können Sie Schemas unter Ziel nicht vorhandenen Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, der während der Synchronisierung erstellt wird.  
  
-   Zuordnung zu SQL Azure  
  
Sie können die Quelldatenbank zuordnen, an das Ziel verbundenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank oder das Schema in der verbundenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Wenn Sie alle nicht vorhandenen Schema unter dem verbundenen Zieldatenbank Quelle Schema zuordnen, Sie werden aufgefordert, mit der Meldung **"das Schema ist in den Metadaten nicht vorhanden. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf "Ja".  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Zurücksetzen auf Ihre ursprüngliche Datenbank und Schema  
Wenn Sie die Zuordnung zwischen einer Access-Datenbank anpassen und ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank und Schema können Sie die Zuordnung in der Datenbank, die Sie angegeben, wenn Sie mit verbunden wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
**Standard-Datenbank und Schema zurücksetzen**  
  
1.  Klicken Sie unter der Registerkarte des Schema-Zuordnung, wählen Sie eine beliebige Zeile, und klicken Sie auf **auf Standard zurücksetzen** wieder in den Standarddatenbank und des Schemas.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [konvertieren Datenbankobjekten](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
