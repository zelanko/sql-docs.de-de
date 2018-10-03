---
title: Zuordnen von DB2- und SQL Server-Datentypen (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e7e939a8-5e76-4509-beaf-5acd1cab505e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 52322c9b3bf9d7b795458e379f5a8db65fcdbdee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739308"
---
# <a name="mapping-db2-and-sql-server-data-types-db2tosql"></a>Zuordnen von DB2- und SQL Server-Datentypen (DB2ToSQL)
DB2-Datenbank unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Datentypen. Bei der Konvertierung zu DB2-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte aufweist, müssen Sie angeben, wie Sie Datentypen aus DB2 in zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können die standardmäßigen datentypzuordnungen übernehmen und die Zuordnungen können angepasst werden, wie in den folgenden Abschnitten gezeigt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA ist einen Standardsatz von datentypzuordnungen. Die Liste der standardzuordnungen, finden Sie unter [Projekteinstellungen &#40;Type Mapping&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="type-mapping-inheritance"></a>Typ zuordnen von Vererbung  
Sie können die replikationsdatentyp-Zuordnungen auf Projektebene, Objekt Category-Ebene (z. B. alle gespeicherten Prozeduren) oder Objektebene anpassen. Einstellungen werden von der höheren Ebene vererbt werden, es sei denn, sie auf einer niedrigeren Ebene überschrieben werden. Wenn Sie zuordnen, z. B. **Smallmoney** zu **Geld** auf Projektebene, werden alle Objekte im Projekt verwenden, diese Zuordnung verwendet werden, es sei denn, die Sie anpassen, dass die Zuordnung auf der Ebene Objekt oder Kategorie.  
  
Beim Anzeigen der **Type Mapping** Registerkarte im Hintergrund SSMA sind farbcodiert, um anzuzeigen, welche typzuordnungen geerbt werden. Der Hintergrund einer Zuordnung ist Gelb für alle geerbten Typ zuordnen und weiß für jede Zuordnung, die auf der aktuellen Ebene angegeben wird.  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentypzuordnungen  
Das folgende Verfahren zeigt, wie Datentypen auf das Projekt, Datenbank oder Objektebene zugeordnet wird:  
  
**Zuordnen von Datentypen**  
  
1.  Öffnen Sie zum Zuordnen von Datentypen für das gesamte Projekt anpassen, die **Projekteinstellungen** Dialogfeld:  
  
    1.  Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen**.  
  
    2.  Wählen Sie im linken Bereich **Type Mapping**.  
  
        Das Diagramm für Typ-Zuordnung und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    Oder zum Anpassen der Datentyp Mapping finden Sie auf die Datenbank, Tabelle, Sicht oder gespeicherte Prozedur auf, wählen Sie die Datenbank, Objektkategorie oder Objekt in DB2-Metadaten-Explorer:  
  
    1.  Wählen Sie im DB2-Metadaten-Explorer den Ordner oder ein Objekt, um anzupassen.  
  
    2.  Klicken Sie im rechten Bereich auf die **Type Mapping** Registerkarte.  
  
2.  Wenn eine neue Zuordnung hinzufügen möchten, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie auf **Hinzufügen**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen den DB2-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** Feld und die maximale Datenlänge in der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** Feld.  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Um eine datentypzuordnung zu ändern, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie auf **Bearbeiten**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen den DB2-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** Feld und die maximale Datenlänge in der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** Feld, und klicken Sie dann [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Um eine benutzerdefinierte datentypzuordnung zu entfernen, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie die Zeile, in der Liste ' datentypzuordnung ', die die Zuordnung von Datentypen enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
        Geerbte Zuordnungen kann nicht entfernt werden. Allerdings werden geerbte Zuordnungen von benutzerdefinierten Zuordnungen in einem bestimmten Objekt bzw. die Objektkategorie überschrieben.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrationsvorgangs besteht entweder [Bewertungsbericht &#40;DB2ToSQL&#41; ](../../ssma/db2/assessment-report-db2tosql.md) oder [Konvertieren von DB2 Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md). Wenn Sie ein Bewertungsbericht erstellen, werden die DB2-Objekten während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
