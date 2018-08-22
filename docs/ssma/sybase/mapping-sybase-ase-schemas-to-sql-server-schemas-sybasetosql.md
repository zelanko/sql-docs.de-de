---
title: Zuordnen von Sybase ASE Schemas in SQL Server-Schemas (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d0f5e75e487b17873a49df25cbf4b4b359ea82b
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395485"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Zuordnen von Sybase ASE-Schemas zu SQL Server-Schemas (SybaseToSQL)
In Sybase Adaptive Server Enterprise (ASE), dass jede Datenbank eine oder mehrere Schemas. Standardmäßig migriert SSMA alle Objekte in einer Datenbank und Schema auf die gleiche Datenbank und das Schema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können jedoch die Zuordnung zwischen der ASE anpassen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbanken und Schemas.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE und SQLServer oder SQL Azure-Schemas  
ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbanken und ihre Schemas mithilfe von zwei Teil Notation als anzugeben *database.schema*. Z. B. in einer ASE **Demo** Datenbank, die möglicherweise eine **Dbo** Schema. Die Datenbank und Schema-Paar, als angegeben sind **demo.dbo**. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure hat die gleiche Datenbank und das Schema, das Paar wird auch als **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und Schema  
Sie können ein Schema für die ASE in SSMA zuordnen, um alle verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Schema.  
  
**So ändern Sie die Datenbank und schema**  
  
1.  Wählen Sie in der Sybase-Metadaten-Explorer, **Datenbanken**.  
  
    Die **Zuordnen von Schemas** Registerkarte ist auch verfügbar, wenn Sie eine einzelne Datenbank, wählen Sie die **Schemas** Ordner oder einzelne Schemas. Die Liste in der **Zuordnen von Schemas** Registerkarte für das ausgewählte Objekt angepasst wird.  
  
2.  Klicken Sie im rechten Bereich auf die **Zuordnen von Schemas** Registerkarte.  
  
    Sie sehen eine Liste aller ASE-Datenbanken mit ihren Schemas, gefolgt von einem Zielwert. Dieses Ziel wird in einer zweiteiligen-Notation angegeben (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, in denen Ihre Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile, die die Zuordnung, die Sie ändern möchten enthält, und klicken Sie dann auf **ändern**.  
  
4.  In der **Zielschema auswählen** im Dialogfeld können Sie für die Zieldatenbank verfügbar und Schema oder mit der Datenbank und des Schemas in das Textfeld in einer zweiteiligen-Schreibweise (database.schema) Namen, und klicken Sie dann auf Durchsuchen **OK**.  
  
5.  Das Ziel geändert werden, auf die **Zuordnen von Schemas** Registerkarte.  
  
**Modi der Zuordnung**  
  
-   Zuordnung zu SQLServer  
  
Sie können die Quelldatenbank zu keiner Zieldatenbank zuordnen. Standardmäßig wird die Quelldatenbank zugeordnet Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Sie verbunden haben, mit der SSMA. Wenn die Zieldatenbank, die zugeordnet wird, auf nicht vorhandene ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann mit einer Meldung werden Sie aufgefordert **"die Datenbank bzw. das Schema ist nicht im Ziel vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen?"** Klicken Sie auf "Ja". Auf ähnliche Weise können Sie Schemas unter Ziel nicht vorhandenen Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, der während der Synchronisierung erstellt wird.  
  
-   Zuordnung zu SQL Azure  
  
Sie können die Quelldatenbank in die verbundene SQL Azure-Zieldatenbank oder eines beliebigen Schemas in der verbundenen SQL Azure-Datenbank zuordnen. Wenn Sie alle nicht vorhandenen Schema unter dem verbundenen Zieldatenbank Quelle Schema zuordnen, Sie werden aufgefordert, mit der Meldung **"das Schema ist in den Metadaten nicht vorhanden. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf "Ja".  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Schemas  
Wenn Sie die Zuordnung zwischen einer ASE anpassen und ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder das Schema der SQL Azure können Sie die Zuordnung zurück auf die Standardwerte wiederherstellen.  
  
**Wieder in den Standarddatenbank und des Schemas**  
  
1.  Klicken Sie unter der Registerkarte des Schema-Zuordnung, wählen Sie eine beliebige Zeile, und klicken Sie auf **auf Standard zurücksetzen** wieder in den Standarddatenbank und des Schemas.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von Sybase ASE-Objekten in analysieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte, können Sie [erstellen Sie einen Konvertierungsbericht](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md). Andernfalls können Sie [konvertieren Sie die ASE Datenbankobjektdefinitionen](converting-sybase-ase-database-objects-sybasetosql.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objektdefinitionen.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
