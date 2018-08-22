---
title: Mapping Oracle Schemas in SQL Server-Schemas (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 5e231fd84b85a44392527e7f082b55da1c7826ac
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396111"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Zuordnen von Oracle-Schemas zu SQL Server-Schemas (OracleToSQL)
In Oracle hat jede Datenbank eine oder mehrere Schemas. Standardmäßig migriert SSMA alle Objekte in einem Oracle-Schema, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Namen für das Schema. Sie können jedoch die Zuordnung zwischen Oracle Schemas anpassen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle und SQL Server-Schemas  
Schemas werden von eine Oracle-Datenbank enthält. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält mehrere Datenbanken, von denen jede kann mehrere Schemas haben.  
  
Das Oracle-Konzept eines Schemas ordnet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konzept für eine Datenbank und eines der Schemas. Z. B. möglicherweise Oracle ein Schema mit dem Namen **HR**. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise eine Datenbank namens **HR**, und innerhalb dieser Datenbank sind Schemas. Ein Schema ist die **Dbo** (oder der Datenbankbesitzer) Schema. Standardmäßig werden Oracle-Schema **HR** zugeordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und Schema **HR.dbo**. SSMA bezieht sich auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kombination von Datenbank und das Schema als ein Schema.  
  
Sie können die Zuordnung zwischen Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und Schema  
Sie können eine Oracle-Schema in SSMA zuordnen, um alle verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema.  
  
**So ändern Sie die Datenbank und schema**  
  
1.  Wählen Sie in der Oracle-Metadaten-Explorer, **Schemas**.  
  
    Die **Zuordnen von Schemas** Registerkarte ist auch verfügbar, wenn Sie eine einzelne Datenbank, wählen Sie die **Schemas** Ordner oder einzelne Schemas. Die Liste in der **Zuordnen von Schemas** Registerkarte für das ausgewählte Objekt angepasst wird.  
  
2.  Klicken Sie im rechten Bereich auf die **Zuordnen von Schemas** Registerkarte.  
  
    Sie sehen eine Liste aller Oracle-Schemas, gefolgt von einem Zielwert. Dieses Ziel wird in einer zweiteiligen-Notation angegeben (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in denen Ihre Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile, die die Zuordnung, die Sie ändern möchten enthält, und klicken Sie dann auf **ändern**.  
  
    In der **Zielschema auswählen** im Dialogfeld können Sie für die Zieldatenbank verfügbar und Schema oder mit der Datenbank und des Schemas in das Textfeld in einer zweiteiligen-Schreibweise (database.schema) Namen, und klicken Sie dann auf Durchsuchen **OK**.  
  
4.  Das Ziel geändert werden, auf die **Zuordnen von Schemas** Registerkarte.  
  
**Modi der Zuordnung**  
  
-   Zuordnung zu SQLServer  
  
Sie können die Quelldatenbank zu keiner Zieldatenbank zuordnen. Standardmäßig wird die Quelldatenbank zugeordnet Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Sie verbunden haben, mit der SSMA. Wenn die Zieldatenbank, die zugeordnet wird, auf nicht vorhandene ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann mit einer Meldung werden Sie aufgefordert **"die Datenbank bzw. das Schema ist nicht im Ziel vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Es wird während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen?"** Klicken Sie auf "Ja". Auf ähnliche Weise können Sie Schemas unter Ziel nicht vorhandenen Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, der während der Synchronisierung erstellt wird.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Schemas  
Wenn Sie die Zuordnung eines Oracle-Schemas anpassen und ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema, Sie können die Zuordnung zurück auf die Standardwerte zurücksetzen.  
  
**Wieder in den Standarddatenbank und des Schemas**  
  
1.  Klicken Sie unter der Registerkarte des Schema-Zuordnung, wählen Sie eine beliebige Zeile, und klicken Sie auf **auf Standard zurücksetzen** wieder in den Standarddatenbank und des Schemas.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von Oracle-Objekten in analysieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte aufweist, können Sie [erstellen Sie einen Konvertierungsbericht](assessing-oracle-schemas-for-conversion-oracletosql.md). Andernfalls können Sie [konvertieren Sie die Oracle-Datenbank-Objektdefinitionen](converting-oracle-schemas-oracletosql.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objektdefinitionen.  
  
## <a name="see-also"></a>Siehe auch  
[Herstellen einer Verbindung mit SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
