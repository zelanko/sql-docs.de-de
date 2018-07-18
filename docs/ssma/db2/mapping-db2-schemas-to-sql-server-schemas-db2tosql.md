---
title: Mapping DB2 Schemas in SQL Server-Schemas (DB2ToSQL) | Microsoft-Dokumentation
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
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e2a0c56197e2ff935a93fe569cc46c632c5a6821
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983252"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Mapping DB2 Schemas in SQL Server-Schemas (DB2ToSQL)
In DB2 verfügt jede Datenbank eine oder mehrere Schemas. Standardmäßig werden alle Objekte in einer DB2-Schema SSMA migriert ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Datenbank mit dem Namen für das Schema. Sie können jedoch die Zuordnung zwischen DB2 Schemas anpassen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Datenbanken.  
  
## <a name="db2-and-sql-server-schemas"></a>DB2- und SQL Server-Schemas  
Schemas werden von eine DB2-Datenbank enthält. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] enthält mehrere Datenbanken, von denen jede kann mehrere Schemas haben.  
  
Der DB2-Konzept eines Schemas ordnet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Konzept für eine Datenbank und eines der Schemas. Z. B. möglicherweise DB2 ein Schema mit dem Namen **HR**. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] möglicherweise eine Datenbank namens **HR**, und innerhalb dieser Datenbank sind Schemas. Ein Schema ist die **Dbo** (oder der Datenbankbesitzer) Schema. Standardmäßig werden von der DB2-Schema **HR** zugeordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Datenbank und Schema **HR.dbo**. SSMA bezieht sich auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Kombination von Datenbank und das Schema als ein Schema.  
  
Sie können die Zuordnung zwischen DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Schemas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und Schema  
Sie können einem DB2-Schema in SSMA zuordnen, um alle verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Schema.  
  
**So ändern Sie die Datenbank und schema**  
  
1.  Wählen Sie in der DB2-Metadaten-Explorer, **Schemas**.  
  
    Die **Zuordnen von Schemas** Registerkarte ist auch verfügbar, wenn Sie eine einzelne Datenbank, wählen Sie die **Schemas** Ordner oder einzelne Schemas. Die Liste in der **Zuordnen von Schemas** Registerkarte für das ausgewählte Objekt angepasst wird.  
  
2.  Klicken Sie im rechten Bereich auf die **Zuordnen von Schemas** Registerkarte.  
  
    Sie sehen eine Liste aller DB2-Schemas, gefolgt von einem Zielwert. Dieses Ziel wird in einer zweiteiligen-Notation angegeben (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , in denen Ihre Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile, die die Zuordnung, die Sie ändern möchten enthält, und klicken Sie dann auf **ändern**.  
  
    In der **Zielschema auswählen** im Dialogfeld können Sie für die Zieldatenbank verfügbar und Schema oder mit der Datenbank und des Schemas in das Textfeld in einer zweiteiligen-Schreibweise (database.schema) Namen, und klicken Sie dann auf Durchsuchen **OK**.  
  
4.  Das Ziel geändert werden, auf die **Zuordnen von Schemas** Registerkarte.  
  
**Modi der Zuordnung**  
  
-   Zuordnung zu SQLServer  
  
Sie können die Quelldatenbank zu keiner Zieldatenbank zuordnen. Standardmäßig wird die Quelldatenbank zugeordnet Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Datenbank mit dem Sie verbunden haben, mit der SSMA. Wenn die Zieldatenbank, die zugeordnet wird, auf nicht vorhandene ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], und klicken Sie dann mit einer Meldung werden Sie aufgefordert **"die Datenbank bzw. das Schema ist nicht im Ziel vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Metadaten. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen?"** Klicken Sie auf "Ja". Auf ähnliche Weise können Sie Schemas unter Ziel nicht vorhandenen Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Datenbank, der während der Synchronisierung erstellt wird.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Schemas  
Wenn Sie die Zuordnung zwischen einem DB2-Schema anpassen und ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Schema, Sie können die Zuordnung zurück auf die Standardwerte zurücksetzen.  
  
**Wieder in den Standarddatenbank und des Schemas**  
  
1.  Klicken Sie unter der Registerkarte des Schema-Zuordnung, wählen Sie eine beliebige Zeile, und klicken Sie auf **auf Standard zurücksetzen** wieder in den Standarddatenbank und des Schemas.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von DB2-Datenbankobjekte in analysieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Objekte aufweist, können Sie [Data Migration Report (häufig SSMA)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>Siehe auch  
[Herstellen einer Verbindung mit SQLServer &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
