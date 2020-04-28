---
title: Festlegen von Projektoptionen (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2c8d074db2fc1e8a9d29ecf5fdc0405524e9bb1a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020919"
---
# <a name="setting-project-options-sybasetosql"></a>Festlegen von Projektoptionen (SybaseToSQL)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben die Objekt Konvertierung, das Laden von Objekten, SQL Azure, die Benutzeroberfläche und Daten Migrations Einstellungen an. Vergewissern Sie sich, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Konfigurationsoptionen für das Projekt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geeignet sind, bevor Sie Objekte in oder SQL Azure oder Daten in oder SQL Azure migrieren.  
  
SSMA ermöglicht Ihnen das Konfigurieren von Standardoptionen für alle Projekte. Diese Optionen werden auf jedes neue Projekt angewendet, das Sie erstellen. Anschließend können Sie die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Konfigurationsoptionen und-Modi  
SSMA verfügt über fünf Sätze von Projekteinstellungen:  
  
1.  Projektinformationen  
  
2.  Allgemein (Konvertierung, Migration und Erfassung von Daten)  
  
3.  Synchronization  
  
4.  GUI  
  
5.  Typzuordnung  
  
Außerdem stehen vier Modi zum Konfigurieren dieser Einstellungen zur Anwendung:  
  
1.  Standard  
  
2.  Optimistisch  
  
3.  Vollständig  
  
4.  Benutzerdefiniert  
  
Der Standardmodus wird für die meisten Benutzer empfohlen. Der optimistische Modus sorgt für mehr von der aktuellen Sybase-ASE-Syntax (Adaptive Server Enterprise) und ist leichter lesbar. Das Beibehalten der aktuellen Syntax ist jedoch möglicherweise nicht korrekt. Wenn die ASE-Syntax in eine äquivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax konvertiert werden muss, führt der vollständige Modus eine vollständige Konvertierung durch, aber der resultierende Code kann schwieriger zu lesen sein. Im benutzerdefinierten Modus legen Sie die Optionen fest.  
  
Diese Einstellungen werden im Abschnitt "Benutzeroberflächen Referenz" in dieser Dokumentation beschrieben. Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Migrations&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Synchronisierung&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;GUI&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Azure SQL-Datenbank &#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen werden in der SSMA-Konfigurationsdatei gespeichert und auf jedes neue Projekt angewendet, das Sie erstellen.  
  
**So legen Sie Standard Projektoptionen fest**  
  
1.  Wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus.  
  
2.  Verwenden Sie im Dialogfeld **Standard Projekteinstellungen** eines der folgenden Prozeduren:  
  
    -   Wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, klicken Sie unten im linken Bereich auf Allgemein, und wählen Sie dann Konvertierung oder Migration oder SQL Azure aus.  
  
    -   Wählen Sie zum Auswählen eines vordefinierten Modus im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig**aus.  
  
    -   Um benutzerdefinierte Einstellungen anzugeben, wählen Sie einfach die neuen Einstellungen oder Werte aus, oder geben Sie Sie ein.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
Sie können auch die Einstellungen für das aktuelle Projekt anpassen. Diese Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**So passen Sie die Einstellungen für das aktuelle Projekt an**  
  
1.  Wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus.  
  
2.  Verwenden Sie im Dialogfeld **Projekteinstellungen** eines der folgenden Prozeduren:  
  
    -   Wählen Sie zum Auswählen eines vordefinierten Modus im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig**aus.  
  
    -   Um einen benutzerdefinierten Modus anzugeben, wählen Sie im Dropdown Feld **Modus** die Option **Benutzer**definiert aus, wählen Sie im linken Bereich eine Option aus, klicken Sie im rechten Bereich auf die Einstellung oder den Wert, und wählen Sie die neue Einstellung oder den Wert aus, oder geben Sie Sie ein.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Wenn Sie eine benutzerdefinierte Zuordnung der Quell-und Ziel Datentypen durcharbeiten möchten, finden Sie weitere Informationen unter [Mapping Sybase ASE und SQL Server Datentyp &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Andernfalls können Sie die Objekt Definitionen der Sybase-Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter " [umstellen von Sybase ASE-Datenbankobjekten &#40;sybasedesql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
