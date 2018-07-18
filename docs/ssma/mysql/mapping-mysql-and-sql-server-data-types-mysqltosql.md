---
title: Zuordnen von MySQL und SQL Server-Datentypen (MySQLToSQL)) | Microsoft-Dokumentation
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
- Mapping, customize data type mapping
- Mapping, Type mapping
ms.assetid: 14f98054-13b4-4231-a6b0-2452f3b9941d
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4690c8db938d53dd290ce642a7fa4ae3884b2a29
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982562"
---
# <a name="mapping-mysql-and-sql-server-data-types-mysqltosql"></a>Zuordnen von MySQL und SQL Server-Datentypen (MySQLToSQL))
MySQL-Datenbank unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Datenbank-Datentypen. Bei der Konvertierung von MySQL-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Objekte, müssen Sie angeben, das Zuordnen von Datentypen aus MySQL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure. Sie können die standardmäßigen datentypzuordnungen übernehmen und die Zuordnungen können angepasst werden, wie in den folgenden Verfahren dargestellt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA ist einen Standardsatz von datentypzuordnungen. Die Liste der standardzuordnungen, finden Sie unter [Projekteinstellungen &#40;Type Mapping&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
## <a name="type-mapping-inheritance"></a>Typ zuordnen von Vererbung  
Sie können die replikationsdatentyp-Zuordnungen auf Projektebene, Objekt Category-Ebene (z. B. alle gespeicherten Prozeduren) oder Objektebene anpassen. Einstellungen werden von der höheren Ebene vererbt werden, es sei denn, sie auf einer niedrigeren Ebene überschrieben werden. Wenn Sie zuordnen, z. B. **Smallint** zu **Int** auf Projektebene, werden alle Objekte im Projekt verwenden, diese Zuordnung verwendet werden, es sei denn, die Sie anpassen, dass die Zuordnung auf der Ebene Objekt oder Kategorie.  
  
Beim Anzeigen der **Type Mapping** Registerkarte im Hintergrund SSMA sind farbcodiert, um anzuzeigen, welche typzuordnungen geerbt werden. Der Hintergrund einer Zuordnung ist Gelb für alle geerbten Typ zuordnen und weiß für jede Zuordnung, die auf der aktuellen Ebene angegeben wird.  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentypzuordnungen  
  
-   **Zuordnen von Datentypen:**  
  
    Die folgenden Verfahren zeigen, wie Sie Datentypen, die auf das Projekt, Datenbank oder Datenbankebene-Objekt zugeordnet wird:  
  
    1.  Öffnen Sie zum Zuordnen von Datentypen für das gesamte Projekt anpassen, die **Projekteinstellungen** Dialogfeld. Wählen Sie auf das Menü "Extras" **Projekteinstellungen**.  
  
        Wählen Sie im linken Bereich **Type Mapping**. Das Diagramm für Typ-Zuordnung und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    2.  Um datentypzuordnungen auf der Datenbank- oder Tabellenebene anzupassen, wählen Sie die Datenbank oder Tabelle in der MySQL-Metadaten-Explorer aus. Wählen Sie in der MySQL-Metadaten-Explorer den Ordner oder ein Objekt, um anzupassen.  
  
        Klicken Sie im rechten Bereich auf **Type Mapping**.  
  
-   **Wenn eine neue Zuordnung hinzufügen möchten, führen Sie folgende Schritte aus:**  
  
    1.  Klicken Sie im Bereich Type Mapping auf **hinzufügen** .  
  
    2.  Geben Sie der neuen Zuordnung im Dialogfeld unter **Quelltyp**, wählen Sie die MySQL-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Länge für die Zuordnung durch Auswahl der **aus** und **zu** Kontrollkästchen und klicken Sie dann die Werte eingeben.  
  
    4.  Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp. Klicken Sie unter **Zieltyp**, wählen Sie die SQL-Zielserver oder SQL Azure-Datentyp.  
  
        1.  Einige Datentypen erfordern eine Ziel-Datentyplänge. Falls erforderlich, geben Sie die neue Datenlänge in die **ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
        2.  Einige Datentypen erfordern den Zieldatentyp **Genauigkeit** und **Skalierung**. Falls erforderlich, geben Sie der neuen Präzision und skalieren in die **ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
-   **Führen Sie folgende Schritte aus, um eine Zuordnung zu bearbeiten:**  
  
    1.  Klicken Sie im Bereich Type Mapping auf **bearbeiten**.  
  
    2.  Listen Sie in die Zuordnung eines Typs im Dialogfeld unter **Quelltyp**, wählen Sie die MySQL-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Länge für die Zuordnung durch Auswahl der **aus** und **zu** Kontrollkästchen und klicken Sie dann die Werte eingeben.  
  
    Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp. Klicken Sie unter **Zieltyp**, wählen Sie die SQL-Zielserver oder SQL Azure-Datentyp.  
  
    1.  Einige Datentypen erfordern eine Ziel-Datentyplänge. Falls erforderlich, geben Sie die neue Datenlänge in die **ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
    2.  Einige Datentypen erfordern den Zieldatentyp **Genauigkeit** und **Skalierung** . Falls erforderlich, geben Sie der neuen Präzision und skalieren in die **ersetzen durch** ein, und klicken Sie dann auf **OK** .  
  
-   **Um eine datentypzuordnung zu entfernen, führen Sie folgende Schritte aus:**  
  
    1.  Wählen Sie die Zeile in der Liste ' datentypzuordnung ', die die Zuordnung von Datentypen enthält, die Sie entfernen möchten, klicken Sie im Bereich "Zuordnung".  
  
    2.  Klicken Sie auf **Entfernen**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht entweder [erstellen Sie ein Bewertungsbericht](http://msdn.microsoft.com/2a56a003-3b0f-453a-963c-00c9e40933ec) oder [MySQL konvertieren Datenbankobjekten in SQL Server oder SQL Azure-Syntax](http://msdn.microsoft.com/ac21850b-fb32-4704-9985-5759b7c688c7). Wenn Sie einen Bericht erstellen, werden die MySQL-Objekten während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
