---
title: Festlegen von Projektoptionen (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Setting project options,configuration options
ms.assetid: 08820d88-e157-4d49-9401-38580dd7ec2d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 346fcd2ea7f83abcb9a5c23a22cb0eded76acc0e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944680"
---
# <a name="setting-project-options-mysqltosql"></a>Festlegen von Projektoptionen (MySqlToSql)
Für jedes Projekt SSMA können Sie Projekt auf Dokumentebene-Optionen festlegen. Diese Optionen angeben, wie Objekte konvertiert werden, wie Daten migriert werden und Zuordnung von Datentypen für die Quelle, Ziel-Datentypen.  Vor dem Konvertieren von Objekten in SQL Server oder SQL Azure oder Daten zu SQL Server oder SQL Azure migrieren, stellen Sie sicher, dass die Konfigurationsoptionen für das Projekt geeignet sind.  
  
SSMA können Sie die Standardoptionen für alle Projekte zu konfigurieren. Diese Optionen werden auf jedem neuen Projekt angewendet, die Sie erstellen. Sie können dann die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Optionen für die Konfiguration und -Modi  
SSMA verfügt über fünf verschiedene projekteinstellungen:  
  
-   Projektinformationen  
  
-   Allgemein (Konvertierung, Migration und SQL Azure)  
  
-   Synchronization  
  
-   GUI  
  
-   Typzuordnung  
  
Die projekteinstellungen können auf vier Arten konfiguriert werden:  
  
-   Default  
  
-   Optimistisch  
  
-   Vollständig  
  
-   Benutzerdefiniert  
  
Der Standardmodus ist für die meisten Benutzer empfohlen. Der vollständige Modus mehrere der Syntax für die aktuelle MySQL speichert, und ist einfacher zu lesen. Allerdings bleiben die Syntax für aktuelle genau möglicherweise nicht. Wenn die MySQL-Syntax entspricht SQL Server- oder SQL Azure-Syntax konvertiert werden muss, wird von der vollständige Modus für die umfassendste Konvertierung durchgeführt. Der resultierende Code, möglicherweise jedoch schwieriger zu lesen. In den benutzerdefinierten Modus ist können Sie die Optionen festlegen.  
  
Weitere Informationen über die Einstellungen und wie die Einstellungen in den einzelnen Modi angewendet werden finden Sie unter den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Migration&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md)  
  
-   [Project Settings (GUI) (SSMA Allgemein)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Synchronisierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Azure SQL-Datenbank&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen sind in der SSMA-Konfigurationsdatei gespeichert und angewendet werden, um neue Projekte, die Sie erstellen.  
  
**Projektoptionen festlegen**  
  
1.  Auf der **Tools** Menü klicken Sie auf **Projekt Standardeinstellungen**.  
  
2.  In der **Projekt Standardeinstellungen** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    1.  Wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden, **Migration Zielversion** Dropdown-Liste, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen **Konvertierung oder Migration oder SQL Azure** Option.  
  
    2.  Wählen Sie zum Auswählen eines vordefinierten Modus **Standard**, **Optimistic**, oder **vollständige** aus der **Modus** Dropdown-Listenfeld.  
  
    3.  Um benutzerdefinierte Einstellungen festzulegen, wählen Sie aus, oder geben Sie den neuen Einstellungen oder Werten.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
Sie können auch die Einstellungen für das aktuelle Projekt anpassen. Die Einstellungen auf der aktuellen Projektdatei gespeichert.  
  
**Anpassen der Einstellungen für das aktuelle Projekt**  
  
1.  Auf der **Tools** Menü klicken Sie auf **ProjectSettings**.  
  
2.  In der **ProjectSettings** (Dialogfeld), verwenden Sie eine der folgenden Verfahren:  
  
    1.  Wählen Sie zum Auswählen eines vordefinierten Modus **Standard**, **Optimistic**, oder **vollständige** aus der **Modus** Dropdown-Listenfeld.  
  
    2.  Wählen Sie zum Angeben eines benutzerdefinierten Modus **benutzerdefinierte** aus der **Modus** Dropdown-Listenfeld. Und wählen Sie dann die geeignete projekteinstellungen.  
  
3.  Klicken Sie auf **OK** zum Speichern der Einstellungen.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Andernfalls können Sie die Objektdefinitionen für MySQL-Datenbank in SQL Server oder SQL Azure-Objektdefinitionen konvertieren. Weitere Informationen finden Sie unter [MySQL-Datenbanken konvertieren &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Zuordnen von MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
