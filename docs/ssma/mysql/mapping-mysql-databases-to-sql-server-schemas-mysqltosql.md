---
title: Zuordnen von MySQL-Datenbanken in SQL Server-Schemas (MySQLToSQL)) | Microsoft-Dokumentation
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
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d28d1ddd205d56ad57a0566485c91bc83ac26593
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395930"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Zuordnen von MySQL-Datenbanken zu SQL Server-Schemas (MySqlToSql)
In der Standardeinstellung SSMA für MySQL migriert werden alle Objekte in einer MySQL-Schema in ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank, die mit dem Namen für das Schema. Sie können jedoch anpassen, die Zuordnungen zwischen MySQL-Schemas und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbanken.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL und SQLServer oder SQL Azure-Schemas  
Das MySQL-Konzept eines Schemas wird das SQL Server-Konzept für eine Datenbank und eines der Schemas zugeordnet. SSMA bezieht sich auf die SQL Server-Kombination als Schema der Datenbank und Schema.  
  
Das MySQL-Konzept eines Schemas wird das SQL Server-Konzept für eine Datenbank und eines der Schemas zugeordnet. Z. B. möglicherweise MySQL ein Schema mit dem Namen **HR**. Eine Instanz von SQL Server möglicherweise eine Datenbank namens **HR**, und innerhalb dieser Datenbank sind Schemas. Ein Schema ist die **Dbo** (oder der Datenbankbesitzer) Schema. Standardmäßig ist das MySQL-Schema **HR** zugeordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und Schema **HR.dbo**. SSMA bezieht sich auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kombination von Datenbank und das Schema als ein Schema.  
  
Sie können die Zuordnung zwischen MySQL ändern und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure-Schemas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und Schema  
Sie können ein MySQL-Schema in SSMA zuordnen, um alle verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Schema.  
  
**So ändern Sie die Datenbank und schema**  
  
1.  Wählen Sie im MySQL-Metadaten-Explorer, **Schemas**.  
  
    Die **Zuordnen von Schemas** Registerkarte ist auch verfügbar, wenn Sie einzelne Schemas auswählen. Die Liste in der **Zuordnen von Schemas** Registerkarte für das ausgewählte Objekt angepasst wird.  
  
2.  Klicken Sie im rechten Bereich auf die **Zuordnen von Schemas** Registerkarte.  
  
    Sie sehen eine Liste aller MySQL-Schemas, gefolgt von einem Zielwert. Dieses Ziel wird in einer zweiteiligen-Notation angegeben (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, in denen Ihre Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile, die die Zuordnung, die Sie ändern möchten enthält, und klicken Sie dann auf **ändern**.  
  
    In der **Zielschema auswählen** im Dialogfeld können Sie für die Zieldatenbank verfügbar und Schema oder mit der Datenbank und des Schemas in das Textfeld in einer zweiteiligen-Schreibweise (database.schema) Namen, und klicken Sie dann auf Durchsuchen **OK**.  
  
4.  Das Ziel geändert werden, auf die **Zuordnen von Schemas** Registerkarte.  
  
**Modi der Zuordnung**  
  
-   Zuordnung zu SQLServer  
  
Sie können die Quelldatenbank zu keiner Zieldatenbank zuordnen. Standardmäßig wird die Quelldatenbank zugeordnet Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Sie verbunden haben, mit der SSMA. Wenn die Zieldatenbank, die zugeordnet wird, auf nicht vorhandene ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann mit einer Meldung werden Sie aufgefordert **"die Datenbank bzw. das Schema ist nicht im Ziel vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen?"** Klicken Sie auf "Ja". Auf ähnliche Weise können Sie Schemas unter Ziel nicht vorhandenen Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, der während der Synchronisierung erstellt wird.  
  
-   Zuordnung zu SQL Azure  
  
Sie können die Quelldatenbank zuordnen, an das Ziel verbundenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank oder das Schema in der verbundenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Wenn Sie alle nicht vorhandenen Schema unter dem verbundenen Zieldatenbank Quelle Schema zuordnen, Sie werden aufgefordert, mit der Meldung **"das Schema ist in den Metadaten nicht vorhanden. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf "Ja".  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Schemas  
Wenn Sie die Zuordnung zwischen einem MySQL-Schema und ein SQL Server-Schema anpassen, können Sie die Zuordnung zurück auf die Standardwerte wiederherstellen.  
  
**Wieder in den Standarddatenbank und des Schemas**  
  
1.  Klicken Sie unter der Registerkarte des Schema-Zuordnung, wählen Sie eine beliebige Zeile, und klicken Sie auf **auf Standard zurücksetzen** wieder in den Standarddatenbank und des Schemas.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von MySQL-Objekten in SQL Server oder SQL Azure-Objekte analysieren möchten, können Sie [erstellen Sie einen Konvertierungsbericht](assessing-mysql-databases-for-conversion-mysqltosql.md) andernfalls können Sie [konvertieren Sie die MySQL-Datenbank-Objektdefinitionen](converting-mysql-databases-mysqltosql.md) in SQL Server oder SQL Azure-schemas  
  
## <a name="see-also"></a>Siehe auch  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Herstellen einer Verbindung mit SQLServer &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
