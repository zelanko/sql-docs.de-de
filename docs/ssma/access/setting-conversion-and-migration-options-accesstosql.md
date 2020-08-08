---
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
ms.openlocfilehash: e074f603586afa0322d62872c49abb52fe47f047
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933961"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>Festlegen von Konvertierungs-und Migrations Optionen (accesstosql)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben an, wie Objekte konvertiert werden, wie Daten migriert werden und wie Quell Datentypen den Ziel Datentypen zugeordnet werden. Vergewissern Sie sich, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dass die Konfigurationsoptionen für das Projekt geeignet sind, bevor Sie Objekte in oder SQL Azure oder Daten in oder SQL Azure migrieren.  
  
## <a name="configuration-options-and-modes"></a>Konfigurationsoptionen und-Modi  
SSMA verfügt über vier Sätze von Konfigurationseinstellungen und vier Modi zum Konfigurieren dieser Einstellungen: Standard, vollständig, vollständig und Benutzer definiert. Der Standardmodus wird für die meisten Benutzer empfohlen. Verwenden Sie den optimistischen Modus für einfache Konvertierungen. Verwenden Sie den vollständigen Modus, wenn alle Meldungen angezeigt werden sollen. Im benutzerdefinierten Modus legen Sie die Optionen fest.  
  
Diese Einstellungen werden im Abschnitt "Benutzeroberflächen Verweis" in dieser Dokumentation beschrieben. Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Project Settings (Conversion) (Projekteinstellungen (Konvertierung)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [Projekteinstellungen (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [Projekteinstellungen (GUI)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Projekteinstellungen (Typzuordnung)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [Projekteinstellungen (SQL Azure)](https://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
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
  
