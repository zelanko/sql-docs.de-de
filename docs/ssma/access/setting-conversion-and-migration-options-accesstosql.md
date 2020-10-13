---
description: Festlegen von Konvertierungs-und Migrations Optionen (accesstosql)
title: Festlegen von Konvertierungs-und Migrations Optionen (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, setting options
- migration options
- modes
- options, conversion settings
- project settings
- schemas
ms.assetid: 0a7304df-2f35-4453-96ef-7ac83dea1167
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: cc9a5328095f2ef839eb0c9617798299e46371fd
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987682"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>Festlegen von Konvertierungs-und Migrations Optionen (accesstosql)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben an, wie Objekte konvertiert werden, wie Daten migriert werden und wie Quell Datentypen den Ziel Datentypen zugeordnet werden. Vergewissern Sie sich, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dass die Konfigurationsoptionen für das Projekt geeignet sind, bevor Sie Objekte in oder SQL Azure oder Daten in oder SQL Azure migrieren.  
  
## <a name="configuration-options-and-modes"></a>Konfigurationsoptionen und-Modi  
SSMA verfügt über vier Sätze von Konfigurationseinstellungen und vier Modi zum Konfigurieren dieser Einstellungen: Standard, vollständig, vollständig und Benutzer definiert. Der Standardmodus wird für die meisten Benutzer empfohlen. Verwenden Sie den optimistischen Modus für einfache Konvertierungen. Verwenden Sie den vollständigen Modus, wenn alle Meldungen angezeigt werden sollen. Im benutzerdefinierten Modus legen Sie die Optionen fest.  
  
Diese Einstellungen werden im Abschnitt "Benutzeroberflächen Verweis" in dieser Dokumentation beschrieben. Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Project Settings (Conversion) (Projekteinstellungen (Konvertierung)](./project-settings-conversion-accesstosql.md)  
  
-   [Projekteinstellungen (Migration)](./project-settings-migration-accesstosql.md)  
  
-   [Projekteinstellungen (GUI)](../sybase/project-settings-gui-sybasetosql.md)  
  
-   [Projekteinstellungen (Typzuordnung)](./project-settings-type-mapping-accesstosql.md)  
  
-   [Projekteinstellungen (SQL Azure)](./project-settings-azure-sql-db-accesstosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen werden in der SSMA-Konfigurationsdatei gespeichert und auf jedes neue Projekt angewendet, das Sie erstellen.  
  
**So legen Sie Standard Projektoptionen fest**  
  
1.  Wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus.  
  
2.  Führen Sie im Dialogfeld **Standard Projekteinstellungen** einen der folgenden Schritte aus:  
  
    -   Wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt/geändert werden müssen, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Konvertierung oder Migration oder SQL Azure**aus.  
  
        > [!NOTE]  
        > SQL Azure Option ist auf der Registerkarte **Allgemein** nur verfügbar, wenn der erstellte Projekttyp SQL Azure ist.  
  
    -   Um einen vordefinierten Modus auszuwählen, wählen Sie im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig** aus.  
  
    -   Um einen benutzerdefinierten Modus anzugeben, wählen Sie im Feld **Modus** die Option **Benutzer** definiert aus, wählen Sie im linken Bereich eine Option aus, klicken Sie im rechten Bereich auf die Einstellung oder den Wert, und wählen Sie dann die neue Einstellung oder den Wert aus.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
Sie können auch die Einstellungen für das aktuelle Projekt anpassen. Diese Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**So passen Sie die Einstellungen für das aktuelle Projekt an**  
  
1.  Wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus.  
  
2.  Führen Sie im Dialogfeld **Projekteinstellungen** einen der folgenden Schritte aus:  
  
    -   Um einen vordefinierten Modus auszuwählen, wählen Sie im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig** aus.  
  
    -   Um einen benutzerdefinierten Modus anzugeben, wählen Sie im Feld **Modus** die Option **Benutzer** definiert aus, wählen Sie im linken Bereich eine Option aus, klicken Sie im rechten Bereich auf die Einstellung oder den Wert, und wählen Sie dann die neue Einstellung oder den Wert aus.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md)  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datenbanken finden Sie unter [Zuordnung von Quell-und Ziel Datenbanken](mapping-source-and-target-databases-accesstosql.md) .  
  
-   Andernfalls können Sie die Objekt Definitionen der Access-Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
