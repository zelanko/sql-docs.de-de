---
title: Festlegen von Projektoptionen (SybaseToSQL) | Microsoft-Dokumentation
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
- Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9048eb69fd10cafc97daa91b5cac8571a4240cd0
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394243"
---
# <a name="setting-project-options-sybasetosql"></a>Festlegen von Projektoptionen (SybaseToSQL)
Für jedes SSMA-Projekt können Sie Optionen für Projekt festlegen. Diese Optionen geben objektkonvertierung, Objekt laden, SQL Azure, Benutzeroberfläche und Einstellungen für die Migration von Daten. Bevor Sie Objekte konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure oder Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, stellen Sie sicher, dass die Konfigurationsoptionen für das Projekt geeignet sind.  
  
SSMA können Sie die Standardoptionen für alle Projekte zu konfigurieren. Diese Optionen werden auf jedem neuen Projekt angewendet, die Sie erstellen. Sie können dann die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Optionen für die Konfiguration und -Modi  
SSMA verfügt über fünf verschiedene projekteinstellungen:  
  
1.  Projektinformationen  
  
2.  Allgemein (Konvertierung, Migration und das Sammeln von Daten)  
  
3.  Synchronization  
  
4.  GUI  
  
5.  Typzuordnung  
  
Es verfügt auch über vier Modi zum Konfigurieren dieser Einstellungen:  
  
1.  Default  
  
2.  Optimistisch  
  
3.  Vollständig  
  
4.  Benutzerdefiniert  
  
Der Standardmodus ist für die meisten Benutzer empfohlen. Der vollständige Modus hält mehrere der Syntax für die aktuelle Sybase Adaptive Server Enterprise (ASE), und es ist einfacher zu lesen. Allerdings bleiben die Syntax für aktuelle genau möglicherweise nicht. Wenn die ASE-Syntax muss, in entsprechende konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den vollständigen Modus für SQL Azure-Syntax führt eine Konvertierung abgeschlossene, aber möglicherweise ist des resultierenden Codes schwieriger zu lesen. In den benutzerdefinierten Modus legen Sie die Optionen an.  
  
Die Einstellungen werden in der Referenz zur Benutzeroberfläche-Abschnitt der Dokumentation beschrieben. Weitere Informationen über die Einstellungen und wie die Einstellungen in den einzelnen Modi angewendet werden finden Sie unter den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Synchronisierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Azure SQL-Datenbank &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen sind in der SSMA-Konfigurationsdatei gespeichert und angewendet werden, um neue Projekte, die Sie erstellen.  
  
**Projektoptionen festlegen**  
  
1.  Auf der **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**.  
  
2.  In der **Projekt Standardeinstellungen** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    -   Wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, um angezeigt oder geändert werden, von **Zielversion für die Migration** löschen nach unten auf Allgemein am unteren Rand im linken Bereich, und wählen Sie dann die Konvertierung oder Migration oder SQL Azure.  
  
    -   Auswählen einen vordefinierten-Modus in den **Modus** wählen Sie im Dropdown- **Standard**, **Optimistic**, oder **vollständige**.  
  
    -   Um benutzerdefinierte Einstellungen anzugeben, wählen Sie einfach, oder geben Sie den neuen Einstellungen oder Werten an.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
Sie können auch Einstellungen für das aktuelle Projekt anpassen. Diese Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**Anpassen der Einstellungen für das aktuelle Projekt**  
  
1.  Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen**.  
  
2.  In der **Projekteinstellungen** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    -   Auswählen einen vordefinierten-Modus in den **Modus** wählen Sie im Dropdown- **Standard**, **Optimistic**, oder **vollständige**.  
  
    -   An einen benutzerdefinierten Modus, in der **Modus** wählen Sie im Dropdownfeld **benutzerdefinierte**, wählen Sie eine Option im linken Bereich, klicken Sie auf die Einstellung oder einen Wert im rechten Bereich, und klicken Sie dann eingeben oder Auswählen der neuen Einstellung oder Wert.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Zu benutzerdefinierten die Zuordnung von Quelle und Ziel-Datentypen, finden Sie unter [Mapping Sybase ASE als auch SQL Server-Datentypen &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Andernfalls können Sie die Objektdefinitionen für Sybase-Datenbank in konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objektdefinitionen. Weitere Informationen finden Sie unter [Konvertieren von Sybase ASE Database Objects &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
