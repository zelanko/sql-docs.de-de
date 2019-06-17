---
title: Zuordnen von Sybase ASE und SQL Server-Datentypen (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8e50253b7c7fb6c59b4303c528c1ef7267ccf644
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62706070"
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Zuordnen von Sybase ASE- und SQL Server-Datentypen (SybaseToSQL)
Datenbank-Datentypen von Sybase Adaptive Server Enterprise (ASE) unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank-Datentypen. Bei der Konvertierung der ASE-Datenbankobjekten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte, müssen Sie angeben, wie Sie Datentypen aus der App Service-Umgebung zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können die standardmäßigen datentypzuordnungen übernehmen und die Zuordnungen können angepasst werden, wie in den folgenden Abschnitten gezeigt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA ist einen Standardsatz von datentypzuordnungen. Die Liste der standardzuordnungen, finden Sie unter [Projekteinstellungen &#40;Type Mapping&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
## <a name="type-mapping-inheritance"></a>Typ zuordnen von Vererbung  
Sie können die replikationsdatentyp-Zuordnungen auf Projektebene, Objekt Category-Ebene (z. B. alle gespeicherten Prozeduren) oder Objektebene anpassen. Einstellungen werden von der höheren Ebene vererbt werden, es sei denn, die auf einer niedrigeren Ebene überschreiben. Wenn Sie zuordnen, z. B. **Smallmoney** zu **Geld** der Ebene der Projekte werden alle Objekte im Projekt verwenden, diese Zuordnung verwendet werden, es sei denn, die Sie anpassen, dass die Zuordnung auf der Objektebene-Kategorie oder Objektebene.  
  
Beim Anzeigen der **Type Mapping** Registerkarte im Hintergrund SSMA sind farbcodiert, um anzuzeigen, welche typzuordnungen geerbt werden. Der Hintergrund einer Zuordnung ist Gelb für alle geerbten Typ zuordnen und weiß, für die Zuordnung angegeben, die auf der aktuellen Ebene.  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentypzuordnungen  
Das folgende Verfahren zeigt, wie Datentypen auf das Projekt, Datenbank oder Objektebene zugeordnet wird.  
  
**Zuordnen von Datentypen**  
  
1.  Öffnen Sie zum Zuordnen von Datentypen für das gesamte Projekt anpassen, die **Projekteinstellungen** Dialogfeld:  
  
    1.  Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen**.  
  
    2.  Wählen Sie im linken Bereich **Type Mapping**.  
  
        Das Diagramm für Typ-Zuordnung und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    Oder zum Anpassen der Datentyp Mapping finden Sie auf die Datenbank, Tabelle, Sicht oder gespeicherte Prozedur auf, wählen Sie die Datenbank, Objektkategorie oder Objekt in Sybase-Metadaten-Explorer:  
  
    1.  Wählen Sie in der Sybase-Metadaten-Explorer den Ordner oder ein Objekt, das Sie anpassen möchten.  
  
    2.  Klicken Sie im rechten Bereich auf die **Type Mapping** Registerkarte.  
  
2.  Wenn eine neue Zuordnung hinzufügen möchten, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie auf **Hinzufügen**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen Sie die ASE-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** , und geben Sie die maximale Datenlänge für die Zuordnung im der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** Feld.  
  
    5.  Klicken Sie auf **OK**.  
  
3.  Führen Sie folgende Schritte aus, um eine datentypzuordnung zu bearbeiten:  
  
    1.  Klicken Sie auf **Bearbeiten**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen Sie die ASE-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** , und geben Sie die maximale Datenlänge für die Zuordnung im der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** ein, und klicken Sie dann auf **OK**.  
  
4.  Um eine benutzerdefinierte datentypzuordnung zu entfernen, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie die Zeile, in der Liste ' datentypzuordnung ', die die Zuordnung von Datentypen enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
        Geerbte Zuordnungen kann nicht entfernt werden. Allerdings werden geerbte Zuordnungen von benutzerdefinierten Zuordnungen in einem bestimmten Objekt bzw. die Objektkategorie überschrieben.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrationsvorgangs besteht entweder [erstellen Sie ein Bewertungsbericht](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) oder [Konvertieren von Sybase ASE-Datenbankobjekten in SQL Server oder SQL Azure-Syntax](converting-sybase-ase-database-objects-sybasetosql.md). Wenn Sie ein Bewertungsbericht erstellen, werden die Sybase ASE-Objekte während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
