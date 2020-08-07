---
title: Zuordnung von MySQL-Datenbanken zu SQL Server Schemas (mysqlto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie SSMA für MySQL-Zuordnungen zwischen MySQL-Schemas und SQL Server oder Azure SQL-Datenbank anpassen oder die Standardeinstellung übernehmen.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5fa0585a82a7c96fac8992b82f631364c27d3b87
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823633"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Zuordnen von MySQL-Datenbanken zu SQL Server-Schemas (MySqlToSql)
Standardmäßig migriert SSMA für MySQL alle Objekte in einem MySQL-Schema zu einer- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Datenbank mit dem Namen für das Schema. Sie können jedoch die Zuordnung zwischen MySQL-Schemas und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbanken anpassen.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL-und SQL Server-oder SQL Azure Schemas  
Das MySQL-Konzept eines Schemas wird dem SQL Server Konzept einer Datenbank und einem ihrer Schemas zugeordnet. SSMA bezieht sich auf die SQL Server Kombination von Datenbank und Schema als Schema.  
  
Das MySQL-Konzept eines Schemas wird dem SQL Server Konzept einer Datenbank und einem ihrer Schemas zugeordnet. Beispielsweise kann MySQL ein Schema mit dem Namen **HR**aufweisen. Eine Instanz von SQL Server könnte eine Datenbank mit dem Namen **HR**aufweisen, und innerhalb dieser Datenbank sind Schemas. Ein Schema ist das **dbo** -Schema (oder das Datenbankbesitzer Schema). Standardmäßig wird das MySQL-Schema **HR** der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und dem Schema **HR. dbo**zugeordnet. SSMA bezieht sich auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kombination von Datenbank und Schema als Schema.  
  
Sie können die Zuordnung zwischen MySQL-und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure-Schemas ändern.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und des Schemas  
In SSMA können Sie einem beliebigen verfügbaren oder SQL Azure Schema ein MySQL-Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**So ändern Sie die Datenbank und das Schema**  
  
1.  Wählen Sie im MySQL-metadatenexplorer **Schemas**aus.  
  
    Die Registerkarte **Schema Zuordnung** ist auch verfügbar, wenn Sie einzelne Schemas auswählen. Die Liste auf der Registerkarte **Schema Zuordnung** ist für das ausgewählte Objekt angepasst.  
  
2.  Klicken Sie im rechten Bereich auf die Registerkarte **Schema Zuordnung** .  
  
    Es wird eine Liste aller MySQL-Schemas angezeigt, gefolgt von einem Zielwert. Dieses Ziel wird in einer zwei teiligen Schreibweise (*Database. Schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, in der die Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile aus, die die Zuordnung enthält, die Sie ändern möchten, und klicken Sie dann auf **ändern**.  
  
    Im Dialogfeld **Ziel Schema auswählen** können Sie nach verfügbaren Ziel Datenbanken und-Schemas suchen oder die Datenbank und den Schema Namen in das Textfeld in einer zwei teiligen Schreibweise (Database. Schema) eingeben und dann auf **OK**klicken.  
  
4.  Das Ziel ändert sich auf der Registerkarte **Schema Zuordnung** .  
  
**Karten Modi**  
  
-   Zuordnung zu SQL Server  
  
Sie können Quell Datenbanken einer beliebigen Zieldatenbank zuordnen. Standardmäßig ist die Quelldatenbank der Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank zugeordnet, mit der Sie eine Verbindung mit SSMA hergestellt haben. Wenn die zugeordnete Zieldatenbank nicht in vorhanden ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird eine Meldung angezeigt, dass **die Datenbank und/oder das Schema in den Ziel Metadaten nicht vorhanden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Es würde während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf „Ja“. Entsprechend können Sie das Schema einem nicht vorhandenen Schema unter der Zieldatenbank zuordnen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das während der Synchronisierung erstellt wird.  
  
-   Zuordnung zu SQL Azure  
  
Sie können die Quelldatenbank der verbundenen Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank oder dem beliebigen Schema in der verbundenen Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank zuordnen. Wenn Sie das Quell Schema einem nicht vorhandenen Schema unter der verbundenen Zieldatenbank zuordnen, wird die Meldung angezeigt, dass **das Schema in den Ziel Metadaten nicht vorhanden ist. Es würde während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf Ja.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Standard Schemas  
Wenn Sie die Zuordnung zwischen einem MySQL-Schema und einem SQL Server Schema anpassen, können Sie die Zuordnung auf die Standardwerte zurücksetzen.  
  
**So setzen Sie die Standarddatenbank und das Standardschema zurück**  
  
1.  Wählen Sie auf der Registerkarte Schema Zuordnung eine beliebige Zeile aus, und klicken Sie auf **Standard zurücksetzen** , um die Standarddatenbank und das Standardschema wiederherzustellen.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von MySQL-Objekten in SQL Server oder SQL Azure Objekte analysieren möchten, können Sie [einen Konvertierungs Bericht erstellen](assessing-mysql-databases-for-conversion-mysqltosql.md) , andernfalls können Sie [die MySQL-Datenbankobjekt Definitionen](converting-mysql-databases-mysqltosql.md) in SQL Server oder SQL Azure Schemas konvertieren.  
  
## <a name="see-also"></a>Weitere Informationen  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;mysqltoisql-&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Herstellen einer Verbindung mit SQL Server &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
