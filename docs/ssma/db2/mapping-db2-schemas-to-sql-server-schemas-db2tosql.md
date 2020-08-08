---
title: Zuordnung von DB2-Schemas zu SQL Server Schemas (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ed1535a9e8af398b9cac7742ab955822cb6034d0
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87936866"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Zuordnung von DB2-Schemas zu SQL Server Schemas (DB2ToSQL)
In DB2 verfügt jede Datenbank über ein oder mehrere Schemas. Standardmäßig migriert SSMA alle Objekte in einem DB2-Schema zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Namen für das Schema. Sie können jedoch die Zuordnung zwischen DB2-Schemas und- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken anpassen.  
  
## <a name="db2-and-sql-server-schemas"></a>DB2-und SQL Server Schemas  
Eine DB2-Datenbank enthält Schemas. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält mehrere Datenbanken, von denen jede über mehrere Schemas verfügen kann.  
  
Das DB2-Konzept eines Schemas wird dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konzept einer Datenbank und einem ihrer Schemas zugeordnet. DB2 könnte beispielsweise über ein Schema mit dem Namen **HR**verfügen. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann eine Datenbank mit dem Namen **HR**aufweisen, und innerhalb dieser Datenbank sind Schemas. Ein Schema ist das **dbo** -Schema (oder das Datenbankbesitzer Schema). Standardmäßig wird die DB2-Schema- **Personalabteilung** der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und dem Schema **HR. dbo**zugeordnet. SSMA bezieht sich auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kombination von Datenbank und Schema als Schema.  
  
Sie können die Zuordnung zwischen DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas ändern.  
  
## <a name="modifying-the-target-database-and-schema"></a>Ändern der Zieldatenbank und des Schemas  
In SSMA können Sie einem beliebigen verfügbaren Schema ein DB2-Schema zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**So ändern Sie die Datenbank und das Schema**  
  
1.  Wählen Sie im DB2-metadatenexplorer **Schemas**aus.  
  
    Die Registerkarte **Schema Zuordnung** ist auch verfügbar, wenn Sie eine einzelne Datenbank, den Ordner **Schemas** oder einzelne Schemas auswählen. Die Liste auf der Registerkarte **Schema Zuordnung** ist für das ausgewählte Objekt angepasst.  
  
2.  Klicken Sie im rechten Bereich auf die Registerkarte **Schema Zuordnung** .  
  
    Es wird eine Liste aller DB2-Schemas angezeigt, gefolgt von einem Zielwert. Dieses Ziel ist in einer zwei teiligen Schreibweise (*Database. Schema*) angegeben, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der die Objekte und Daten migriert werden.  
  
3.  Wählen Sie die Zeile aus, die die Zuordnung enthält, die Sie ändern möchten, und klicken Sie dann auf **ändern**.  
  
    Im Dialogfeld **Ziel Schema auswählen** können Sie nach verfügbaren Ziel Datenbanken und-Schemas suchen oder die Datenbank und den Schema Namen in das Textfeld in einer zwei teiligen Schreibweise (Database. Schema) eingeben und dann auf **OK**klicken.  
  
4.  Das Ziel ändert sich auf der Registerkarte **Schema Zuordnung** .  
  
**Karten Modi**  
  
-   Zuordnung zu SQL Server  
  
Sie können Quell Datenbanken einer beliebigen Zieldatenbank zuordnen. Standardmäßig ist die Quelldatenbank der Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank zugeordnet, mit der Sie eine Verbindung mit SSMA hergestellt haben. Wenn die zugeordnete Zieldatenbank nicht in vorhanden ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird eine Meldung angezeigt, dass **die Datenbank und/oder das Schema in den Ziel Metadaten nicht vorhanden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Es würde während der Synchronisierung erstellt werden. Möchten Sie den Vorgang fortsetzen? "** Klicken Sie auf „Ja“. Entsprechend können Sie das Schema einem nicht vorhandenen Schema unter der Zieldatenbank zuordnen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das während der Synchronisierung erstellt wird.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Wiederherstellen der Standarddatenbank und des Standard Schemas  
Wenn Sie die Zuordnung zwischen einem DB2-Schema und einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schema anpassen, können Sie die Zuordnung auf die Standardwerte zurücksetzen.  
  
**So setzen Sie die Standarddatenbank und das Standardschema zurück**  
  
1.  Wählen Sie auf der Registerkarte Schema Zuordnung eine beliebige Zeile aus, und klicken Sie auf **Standard zurücksetzen** , um die Standarddatenbank und das Standardschema wiederherzustellen.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Konvertierung von DB2-Objekten in Objekte analysieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie [Daten Migrationsbericht (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>Weitere Informationen  
[Herstellen einer Verbindung mit SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Migrieren von DB2-Datenbanken zu SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
