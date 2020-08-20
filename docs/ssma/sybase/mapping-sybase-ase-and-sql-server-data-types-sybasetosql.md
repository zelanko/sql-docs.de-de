---
description: Zuordnen von Sybase ASE- und SQL Server-Datentypen (SybaseToSQL)
title: Zuordnung von Sybase ASE und SQL Server Datentypen (sybasetosql) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5a7e1ba17822d339e5ae40e6e6b5828191ce84ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463172"
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Zuordnen von Sybase ASE- und SQL Server-Datentypen (SybaseToSQL)
Die Datenbanktypen von Sybase Adaptive Server Enterprise (ASE) unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL-Datenbanktypen. Beim Konvertieren von ASE-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte müssen Sie angeben, wie Datentypen von ASE zu oder SQL Azure zugeordnet werden sollen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können die standardmäßigen Datentyp Zuordnungen akzeptieren, oder Sie können die Zuordnungen anpassen, wie in den folgenden Abschnitten dargestellt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA verfügt über einen Standardsatz von Datentyp Zuordnungen. Die Liste der Standard Zuordnungen finden Sie unter [Project Settings &#40;Type Mapping&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
## <a name="type-mapping-inheritance"></a>Vererbung der Typzuordnung  
Sie können Typzuordnungen auf Projektebene, Objekt Kategorieebene (z. b. alle gespeicherten Prozeduren) oder auf Objektebene anpassen. Die Einstellungen werden von der höheren Ebene geerbt, sofern Sie nicht auf einer niedrigeren Ebene überschrieben werden. Wenn Sie z. b. **smallmoney** Money **auf der** Projektebene zuordnen, verwenden alle Objekte im Projekt diese Zuordnung, es sei denn, Sie passen die Zuordnung auf Objekt Kategorieebene oder Objektebene an.  
  
Wenn Sie die Registerkarte **Typzuordnung** in SSMA anzeigen, ist der Hintergrund Farb codiert, um anzuzeigen, welche Typzuordnungen geerbt werden. Der Hintergrund einer Typzuordnung ist für jede geerbte Typzuordnung gelb und weiß für jede auf der aktuellen Ebene angegebene Zuordnung.  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentyp Zuordnungen  
Im folgenden Verfahren wird gezeigt, wie Datentypen auf Projekt-, Datenbank-oder Objektebene zugeordnet werden.  
  
**So ordnen Sie Datentypen zu**  
  
1.  Um die Datentyp Zuordnung für das gesamte Projekt anzupassen, öffnen Sie das Dialogfeld **Projekteinstellungen** :  
  
    1.  Wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus.  
  
    2.  Wählen Sie im linken Bereich **Typzuordnung**aus.  
  
        Das Typmapping-Diagramm und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    Wenn Sie die Datentyp Zuordnung auf Datenbank-, Tabellen-, Sicht-oder gespeicherter Prozedur anpassen möchten, wählen Sie im Sybase-metadatenexplorer die Datenbank, die Objekt Kategorie oder das Objekt aus:  
  
    1.  Wählen Sie im Sybase-metadatenexplorer den Ordner oder das Objekt aus, den bzw. das Sie anpassen möchten.  
  
    2.  Klicken Sie im rechten Bereich auf die Registerkarte **Typzuordnung** .  
  
2.  Gehen Sie folgendermaßen vor, um eine neue Zuordnung hinzuzufügen:  
  
    1.  Klicken Sie auf **Hinzufügen**.  
  
    2.  Wählen Sie unter **Quelltyp**den zu zuordnenden ASE-Datentyp aus.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie im Feld **von** die minimale Daten Länge für die Zuordnung an, und geben Sie im Feld **an** die maximale Daten Länge für die Zuordnung an.  
  
        Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen.  
  
    4.  Wählen Sie unter **Zieltyp**das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den SQL Azure Datentyp aus.  
  
        Einige Typen erfordern eine Länge des Ziel Datentyps. Wenn dies erforderlich ist, geben Sie die neue Daten Länge in das Feld **Ersetzen durch** ein.  
  
    5.  Klicken Sie auf **OK**.  
  
3.  Gehen Sie folgendermaßen vor, um eine Datentyp Zuordnung zu bearbeiten:  
  
    1.  Klicken Sie auf **Bearbeiten**.  
  
    2.  Wählen Sie unter **Quelltyp**den zu zuordnenden ASE-Datentyp aus.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie im Feld **von** die minimale Daten Länge für die Zuordnung an, und geben Sie im Feld **an** die maximale Daten Länge für die Zuordnung an.  
  
        Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen.  
  
    4.  Wählen Sie unter **Zieltyp**das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den SQL Azure Datentyp aus.  
  
        Einige Typen erfordern eine Länge des Ziel Datentyps. Wenn dies erforderlich ist, geben Sie die neue Daten Länge im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
4.  Gehen Sie folgendermaßen vor, um eine benutzerdefinierte Datentyp Zuordnung zu entfernen:  
  
    1.  Wählen Sie die Zeile in der Liste Typzuordnung aus, die die Datentyp Zuordnung enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
        Geerbte Zuordnungen können nicht entfernt werden. Geerbte Zuordnungen werden jedoch von benutzerdefinierten Zuordnungen für ein bestimmtes Objekt oder eine bestimmte Objekt Kategorie überschrieben.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrations Vorgangs besteht darin, entweder [einen Bewertungsbericht zu erstellen](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) oder [Sybase-ASE-Datenbankobjekte in SQL Server-oder SQL Azure-Syntax zu konvertieren](converting-sybase-ase-database-objects-sybasetosql.md). Wenn Sie einen Bewertungsbericht erstellen, werden die Sybase-ASE-Objekte während der Bewertung automatisch konvertiert.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
