---
title: Zuordnen von Oracle- und SQL Server-Datentypen (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Type Mapping Inheritance
ms.assetid: 05da1495-63b9-47b7-86e2-6746394a2d8a
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 06e538ebbdab9d6438182eaa0b61d44818286547
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796024"
---
# <a name="mapping-oracle-and-sql-server-data-types-oracletosql"></a>Zuordnen von Oracle- und SQL Server-Datentypen (OracleToSQL)
Oracle-Datenbank unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Datentypen. Bei der Konvertierung zu Oracle-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte aufweist, müssen Sie angeben, das Zuordnen von Datentypen aus Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können die standardmäßigen datentypzuordnungen übernehmen und die Zuordnungen können angepasst werden, wie in den folgenden Abschnitten gezeigt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA ist einen Standardsatz von datentypzuordnungen. Die Liste der standardzuordnungen, finden Sie unter [Projekteinstellungen &#40;Type Mapping&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
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
  
    Oder zum Anpassen der Datentyp Mapping finden Sie auf die Datenbank, Tabelle, Sicht oder gespeicherte Prozedur auf, wählen Sie die Datenbank, Objektkategorie oder Objekt in der Oracle-Metadaten-Explorer:  
  
    1.  Wählen Sie in der Oracle-Metadaten-Explorer den Ordner oder ein Objekt, um anzupassen.  
  
    2.  Klicken Sie im rechten Bereich auf die **Type Mapping** Registerkarte.  
  
2.  Wenn eine neue Zuordnung hinzufügen möchten, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie auf **Hinzufügen**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen Sie den Oracle-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** Feld und die maximale Datenlänge in der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** Feld.  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Um eine datentypzuordnung zu ändern, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie auf **Bearbeiten**.  
  
    2.  Klicken Sie unter **Quelltyp**, wählen Sie den Oracle-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimale Datenlänge für die Zuordnung in der **aus** Feld und die maximale Datenlänge in der **zu** Feld.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen Sie dies durch** Feld, und klicken Sie dann [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Um eine benutzerdefinierte datentypzuordnung zu entfernen, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie die Zeile, in der Liste ' datentypzuordnung ', die die Zuordnung von Datentypen enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
        Geerbte Zuordnungen kann nicht entfernt werden. Allerdings werden geerbte Zuordnungen von benutzerdefinierten Zuordnungen in einem bestimmten Objekt bzw. die Objektkategorie überschrieben.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrationsvorgangs besteht entweder [erstellen Sie ein Bewertungsbericht](assessing-oracle-schemas-for-conversion-oracletosql.md) oder [konvertieren Sie Objekte des Oracle-Datenbank in SQL Server-Syntax](converting-oracle-schemas-oracletosql.md). Wenn Sie ein Bewertungsbericht erstellen, werden die Oracle-Objekte während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
