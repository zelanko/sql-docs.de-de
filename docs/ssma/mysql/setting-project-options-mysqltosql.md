---
description: Festlegen von Projektoptionen (MySqlToSql)
title: Festlegen von Projektoptionen (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Setting project options,configuration options
ms.assetid: 08820d88-e157-4d49-9401-38580dd7ec2d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: df2a29b2d411c2502573ede95feefe9c1e061c5b
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987896"
---
# <a name="setting-project-options-mysqltosql"></a>Festlegen von Projektoptionen (MySqlToSql)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben an, wie Objekte konvertiert werden, wie Daten migriert werden und wie Quell Datentypen den Ziel Datentypen zugeordnet werden.  Überprüfen Sie vor dem Konvertieren von Objekten in SQL Server oder SQL Azure oder Migrieren von Daten in SQL Server oder SQL Azure, ob die Konfigurationsoptionen für das Projekt geeignet sind.  
  
SSMA ermöglicht Ihnen das Konfigurieren der Standardoptionen für alle Projekte. Diese Optionen werden auf jedes neue Projekt angewendet, das Sie erstellen. Anschließend können Sie die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Konfigurationsoptionen und-Modi  
SSMA verfügt über fünf Sätze von Projekteinstellungen:  
  
-   Projektinformationen  
  
-   Allgemein (Konvertierung, Migration und SQL Azure)  
  
-   Synchronization  
  
-   GUI  
  
-   Typzuordnung  
  
Die Projekteinstellungen können auf vier Arten konfiguriert werden:  
  
-   Standard  
  
-   Optimistisch  
  
-   Vollständig  
  
-   Benutzerdefiniert  
  
Der Standardmodus wird für die meisten Benutzer empfohlen. Der optimistische Modus behält mehr die aktuelle MySQL-Syntax bei und ist leichter lesbar. Das Beibehalten der aktuellen Syntax ist jedoch möglicherweise nicht korrekt. Wenn die MySQL-Syntax in eine äquivalente SQL Server oder SQL Azure Syntax konvertiert werden muss, führt der vollständige Modus die vollständigste Konvertierung durch. Der resultierende Code kann jedoch schwieriger zu lesen sein. Im benutzerdefinierten Modus können Sie die Optionen festlegen.  
  
Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;mysqltoisql-&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Migration&#41; &#40;mysqldesql-&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md)  
  
-   [Projekteinstellungen (GUI) (SSMA Common)](../sybase/project-settings-gui-sybasetosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;mysqldesql-&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Synchronisierung&#41; &#40;mysqldesql&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
-   [Projekteinstellungen &#40;Azure SQL-Datenbank&#41; &#40;mysqldesql&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen werden in der SSMA-Konfigurationsdatei gespeichert und auf jedes neue Projekt angewendet, das Sie erstellen.  
  
**So legen Sie Standard Projektoptionen fest**  
  
1.  Klicken Sie **im Menü Extras** auf **Standard Projekteinstellungen**.  
  
2.  Verwenden Sie im Dialogfeld **Standard Projekteinstellungen** eines der folgenden Prozeduren:  
  
    1.  Wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt/geändert werden müssen, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Konvertierung oder Migration oder SQL Azure** Option aus.  
  
    2.  Um einen vordefinierten Modus auszuwählen, wählen Sie im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig** aus.  
  
    3.  Zum Angeben benutzerdefinierter Einstellungen wählen Sie die neuen Einstellungen oder Werte aus, oder geben Sie Sie ein.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
Sie können auch die Einstellungen für das aktuelle Projekt anpassen. Die Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**So passen Sie die Einstellungen für das aktuelle Projekt an**  
  
1.  Klicken Sie **im Menü Extras** auf **ProjectSettings**.  
  
2.  Verwenden Sie im Dialogfeld **ProjectSettings** eines der folgenden Prozeduren:  
  
    1.  Um einen vordefinierten Modus auszuwählen, wählen Sie im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig** aus.  
  
    2.  Um einen benutzerdefinierten Modus anzugeben, wählen Sie im Dropdown Feld **Modus** die Option **Benutzer** definiert aus. Und wählen Sie dann die entsprechenden Projekteinstellungen aus.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping MySQL and SQL Server Data Types &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Andernfalls können Sie die MySQL-Datenbankobjekt Definitionen in SQL Server oder SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von MySQL-Datenbanken &#40;mysqlto SQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Zuordnung von MySQL-und SQL Server Datentypen &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
