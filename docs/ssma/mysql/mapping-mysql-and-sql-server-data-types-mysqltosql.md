---
title: Zuordnung von MySQL-und SQL Server-Datentypen (mysqltosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping, customize data type mapping
- Mapping, Type mapping
ms.assetid: 14f98054-13b4-4231-a6b0-2452f3b9941d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 604f9ce8e26e3d2221cd9a4bf7732c56ba3296c0
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935356"
---
# <a name="mapping-mysql-and-sql-server-data-types-mysqltosql"></a>Zuordnen von MySQL- und SQL Server-Datentypen (MySqlToSql)
MySQL-Datenbanktypen unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL-Datenbanktypen. Beim Konvertieren von MySQL-Datenbankobjekten in- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure-Objekte müssen Sie angeben, wie Datentypen von MySQL zu oder SQL Azure zugeordnet werden sollen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können die standardmäßigen Datentyp Zuordnungen akzeptieren, oder Sie können die Zuordnungen anpassen, wie in den folgenden Prozeduren gezeigt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA verfügt über einen Standardsatz von Datentyp Zuordnungen. Die Liste der Standard Zuordnungen finden Sie unter [Project Settings &#40;Type Mapping&#41; &#40;mysqlto SQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
## <a name="type-mapping-inheritance"></a>Vererbung der Typzuordnung  
Sie können Typzuordnungen auf Projektebene, Objekt Kategorieebene (z. b. alle gespeicherten Prozeduren) oder auf Objektebene anpassen. Die Einstellungen werden von der höheren Ebene geerbt, sofern Sie nicht auf einer niedrigeren Ebene überschrieben werden. Wenn Sie z. b. **smallint** auf Projektebene zu **int** zuordnen, verwenden alle Objekte im Projekt diese Zuordnung, es sei denn, Sie passen die Zuordnung auf Objekt-oder Kategorieebene an.  
  
Wenn Sie die Registerkarte **Typzuordnung** in SSMA anzeigen, ist der Hintergrund Farb codiert, um anzuzeigen, welche Typzuordnungen geerbt werden. Der Hintergrund einer Typzuordnung ist für jede geerbte Typzuordnung gelb und weiß für jede Zuordnung, die auf der aktuellen Ebene angegeben wird.  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentyp Zuordnungen  
  
-   **So ordnen Sie Datentypen zu:**  
  
    Die folgenden Prozeduren zeigen, wie Datentypen auf der Projekt-, Datenbank-oder Datenbankobjekt Ebene zugeordnet werden:  
  
    1.  Um die Datentyp Zuordnung für das gesamte Projekt anzupassen, öffnen Sie das Dialogfeld **Projekteinstellungen** . Wählen Sie im Menü Extras die Option **Projekteinstellungen**aus.  
  
        Wählen Sie im linken Bereich **Typzuordnung**aus. Das Typmapping-Diagramm und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    2.  Um Datentyp Zuordnungen auf Datenbank-oder Tabellenebene anzupassen, wählen Sie die Datenbank oder Tabelle im MySQL-metadatenexplorer aus. Wählen Sie im MySQL-metadatenexplorer den Ordner oder das Objekt aus, der angepasst werden soll.  
  
        Klicken Sie im rechten Bereich auf **Typzuordnung**.  
  
-   **Gehen Sie folgendermaßen vor, um eine neue Zuordnung hinzuzufügen:**  
  
    1.  Klicken Sie im Bereich Typzuordnung auf **Hinzufügen** .  
  
    2.  Wählen Sie im Dialogfeld neue Typzuordnung unter **Quelltyp**den MySQL-Datentyp aus, der zugeordnet werden soll.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Daten Längen für die Zuordnung an, indem Sie die Kontrollkästchen **aus** und **auf** aktivieren und dann die Werte eingeben.  
  
    4.  Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen. Wählen Sie unter **Zieltyp**das Ziel SQL Server oder SQL Azure Datentyp aus.  
  
        1.  Einige Typen erfordern eine Länge des Ziel Datentyps. Geben Sie bei Bedarf die neue Daten Länge im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
        2.  Für einige Typen ist die **Genauigkeit** und **Skalierung**von Ziel Datentypen erforderlich. Geben Sie bei Bedarf die neue Genauigkeit und Skalierung im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
-   **Gehen Sie folgendermaßen vor, um eine Typzuordnung zu bearbeiten:**  
  
    1.  Klicken Sie im Bereich Typzuordnung auf **Bearbeiten**.  
  
    2.  Wählen Sie im Dialogfeld typzuordnungs Liste unter **Quelltyp**den MySQL-Datentyp aus, der zugeordnet werden soll.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Daten Längen für die Zuordnung an, indem Sie die Kontrollkästchen **aus** und **auf** aktivieren und dann die Werte eingeben.  
  
    Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen. Wählen Sie unter **Zieltyp**das Ziel SQL Server oder SQL Azure Datentyp aus.  
  
    -  Einige Typen erfordern eine Länge des Ziel Datentyps. Geben Sie bei Bedarf die neue Daten Länge im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
    -  Für einige Typen ist die **Genauigkeit** und **Skalierung**von Ziel Datentypen erforderlich. Geben Sie bei Bedarf die neue Genauigkeit und Skalierung im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
-   **Gehen Sie folgendermaßen vor, um eine Datentyp Zuordnung zu entfernen:**  
  
    1.  Wählen Sie im Bereich Typzuordnung die Zeile in der Liste Typzuordnung aus, die die Datentyp Zuordnung enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, entweder [einen Bewertungsbericht zu erstellen](assessing-mysql-databases-for-conversion-mysqltosql.md) oder [MySQL-Datenbankobjekte in SQL Server oder SQL Azure-Syntax zu konvertieren](converting-mysql-databases-mysqltosql.md). Wenn Sie einen Bericht erstellen, werden MySQL-Objekte während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
