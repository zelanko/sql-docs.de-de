---
description: Festlegen von Projektoptionen (OracleToSQL)
title: Festlegen von Projektoptionen (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Configuration Options and Modes
ms.assetid: a324d07d-cfdf-43bd-98a0-acf332c5a4db
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 89460a8efb6278d8e4aaa4def6310d6dec687429
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492351"
---
# <a name="setting-project-options-oracletosql"></a>Festlegen von Projektoptionen (OracleToSQL)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben die Objekt Konvertierung, das Laden von Objekten, die Benutzeroberfläche und die Daten Migrations Einstellungen an. Bevor Sie-Objekte in konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Daten in migrieren, müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüfen, ob die Konfigurationsoptionen für das Projekt geeignet sind.  
  
SSMA ermöglicht Ihnen das Konfigurieren von Standardoptionen für alle Projekte. Diese Optionen werden auf jedes neue Projekt angewendet, das Sie erstellen. Anschließend können Sie die Optionen für jedes Projekt anpassen.  
  
## <a name="configuration-options-and-modes"></a>Konfigurationsoptionen und-Modi  
SSMA verfügt über fünf Sätze von Projekteinstellungen:  
  
-   Projektinformationen  
  
-   Allgemein (Konvertierung, Migration, Laden von Objekten)  
  
-   Synchronization  
  
-   GUI  
  
-   Typzuordnung  
  
Außerdem stehen vier Modi zum Konfigurieren dieser Einstellungen zur Anwendung:  
  
-   Standard  
  
-   Optimistisch  
  
-   Vollständig  
  
-   Benutzerdefiniert  
  
Der Standardmodus wird für die meisten Benutzer empfohlen. Der optimistische Modus behält mehr von der aktuellen Oracle-Syntax bei und ist leichter lesbar. Das Beibehalten der aktuellen Syntax ist jedoch möglicherweise nicht korrekt. Wenn die Oracle-Syntax in eine äquivalente Syntax konvertiert werden muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , führt der vollständige Modus die vollständigste Konvertierung durch, aber der resultierende Code kann schwieriger zu lesen sein. Im benutzerdefinierten Modus legen Sie die Optionen fest.  
  
Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;oracleto SQL-&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
-   [Projekteinstellungen &#40;Migration&#41; &#40;oracleto SQL-&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md)  
  
-   [Projekteinstellungen&#40;Synchronisierung&#41; &#40;oracleto SQL-&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md)  
  
-   [Projekteinstellungen &#40;GUI&#41; &#40;oracledesql&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;oracledesql-&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)  
  
## <a name="setting-project-options"></a>Festlegen von Projektoptionen  
In SSMA können Sie die Standardeinstellungen für alle Projekte konfigurieren. Diese Einstellungen werden in der SSMA-Konfigurationsdatei gespeichert und auf jedes neue Projekt angewendet, das Sie erstellen.  
  
**So legen Sie Standard Projektoptionen fest**  
  
1.  Klicken Sie **im Menü Extras** auf **Standard Projekteinstellungen**.  
  
2.  Verwenden Sie im Dialogfeld **Standard Projekteinstellungen** eines der folgenden Prozeduren:  
  
    -   Wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann Konvertierung oder Migration aus.  
  
    -   Wählen Sie zum Auswählen eines vordefinierten Modus im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig**aus.  
  
    -   Zum Angeben benutzerdefinierter Einstellungen wählen Sie die neuen Einstellungen oder Werte aus, oder geben Sie Sie ein.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
Sie können auch die Einstellungen für das aktuelle Projekt anpassen. Diese Einstellungen werden in der aktuellen Projektdatei gespeichert.  
  
**So passen Sie die Einstellungen für das aktuelle Projekt an**  
  
1.  Klicken Sie **im Menü Extras** auf **Projekteinstellungen**.  
  
2.  Verwenden Sie im Dialogfeld **Projekteinstellungen** eines der folgenden Prozeduren:  
  
    -   Wählen Sie zum Auswählen eines vordefinierten Modus im Dropdown Feld **Modus** die Option **Standard**, **optimistische**oder **vollständig**aus.  
  
    -   Um einen benutzerdefinierten Modus anzugeben, wählen Sie im Feld **Modus** die Option **Benutzer**definiert aus, und wählen Sie dann die entsprechenden Projekteinstellungen aus.  
  
3.  Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping von Oracle-und SQL Server-Datentypen &#40;oracletosql-&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
-   Andernfalls können Sie die Definitionen der Oracle-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von Oracle-Schemas &#40;oracleto SQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Zuordnung von Oracle-und SQL Server-Datentypen &#40;oracletosql-&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)  
  
