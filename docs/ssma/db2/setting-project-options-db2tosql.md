---
title: Festlegen von Projektoptionen (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d384433e5a2653291fac4d990bb3660b31c13855
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060035"
---
# <a name="setting-project-options-db2tosql"></a>Festlegen von Projektoptionen (DB2ToSQL)
Für jedes SSMA-Projekt können Sie Optionen für Projekt festlegen. Diese Optionen geben objektkonvertierung, Objekt laden, Benutzer-Schnittstelle und migrationseinstellungen. Bevor Sie Objekte konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], stellen Sie sicher, dass die Konfigurationsoptionen für das Projekt geeignet sind.  
  
SSMA können Sie die Standardoptionen für alle Projekte zu konfigurieren. Diese Optionen werden auf jedem neuen Projekt angewendet, die Sie erstellen. Sie können dann die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Optionen für die Konfiguration und -Modi  
SSMA verfügt über fünf verschiedene projekteinstellungen:  
  
-   Projektinformationen  
  
-   Allgemein (Konvertierung, Migration, und Laden von Objekten)  
  
-   Synchronization  
  
-   GUI  
  
-   Typzuordnung  
  
Es verfügt auch über vier Modi zum Konfigurieren dieser Einstellungen:  
  
-   Default  
  
-   Optimistisch  
  
-   Vollständig  
  
-   Benutzerdefiniert  
  
Der Standardmodus ist für die meisten Benutzer empfohlen. Der vollständige Modus speichert mehrere der Syntax für die aktuelle DB2, und es ist einfacher zu lesen. Allerdings bleiben die Syntax für aktuelle genau möglicherweise nicht. Wenn die DB2-Syntax muss, in entsprechende konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, die den vollständigen Modus für die umfassendste Konvertierung durchgeführt, aber der resultierende Code ist möglicherweise schwieriger zu lesen. In den benutzerdefinierten Modus legen Sie die Optionen an.  
  
Weitere Informationen über die Einstellungen und wie die Einstellungen in den einzelnen Modi angewendet werden finden Sie unter den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [Projekteinstellungen &#40;Migration&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [Projekteinstellungen&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [Projekteinstellungen &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen sind in der SSMA-Konfigurationsdatei gespeichert und angewendet werden, um neue Projekte, die Sie erstellen.  
  
**Projektoptionen festlegen**  
  
1.  Auf der **Tools** Menü klicken Sie auf **Projekt Standardeinstellungen**.  
  
2.  In der **Projekt Standardeinstellungen** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    -   Wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, um angezeigt oder geändert werden, von **Zielversion für die Migration** öffnen Sie auf die Dropdownliste **allgemeine** am unteren Rand der linken Bereich, und wählen Sie dann-Konvertierung oder Die Migration.  
  
    -   Auswählen einen vordefinierten-Modus in den **Modus** wählen Sie im Dropdown- **Standard**, **Optimistic**, oder **vollständige**.  
  
    -   Um benutzerdefinierte Einstellungen festzulegen, wählen Sie aus, oder geben Sie den neuen Einstellungen oder Werten.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
Sie können auch Einstellungen für das aktuelle Projekt anpassen. Diese Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**Anpassen der Einstellungen für das aktuelle Projekt**  
  
1.  Auf der **Tools** Menü klicken Sie auf **Projekteinstellungen**.  
  
2.  In der **Projekteinstellungen** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    -   Auswählen einen vordefinierten-Modus in den **Modus** wählen Sie im Dropdown- **Standard**, **Optimistic**, oder **vollständige**.  
  
    -   An einen benutzerdefinierten Modus, in der **Modus** Kontrollkästchen **benutzerdefinierte**, und wählen Sie dann die geeignete projekteinstellungen.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping DB2- und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Andernfalls können Sie die DB2-Datenbank-Objektdefinitionen in konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objektdefinitionen. Weitere Informationen finden Sie unter [Konvertieren von DB2 Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Zuordnen von DB2- und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
