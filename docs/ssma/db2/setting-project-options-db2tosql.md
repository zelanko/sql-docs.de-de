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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060035"
---
# <a name="setting-project-options-db2tosql"></a>Festlegen von Projektoptionen (DB2ToSQL)
Für jedes SSMA-Projekt können Sie Optionen auf Projektebene festlegen. Diese Optionen geben die Objekt Konvertierung, das Laden von Objekten, die Benutzeroberfläche und die Daten Migrations Einstellungen an. Bevor Sie-Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertieren oder Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren, müssen Sie überprüfen, ob die Konfigurationsoptionen für das Projekt geeignet sind.  
  
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
  
Der Standardmodus wird für die meisten Benutzer empfohlen. Der optimistische Modus behält mehr die aktuelle DB2-Syntax bei und ist leichter lesbar. Das Beibehalten der aktuellen Syntax ist jedoch möglicherweise nicht korrekt. Wenn die DB2-Syntax in eine äquivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax konvertiert werden muss, führt der vollständige Modus die vollständigste Konvertierung durch, aber der resultierende Code kann schwieriger zu lesen sein. Im benutzerdefinierten Modus legen Sie die Optionen fest.  
  
Weitere Informationen zu den Einstellungen und zum Anwenden der Einstellungen in den einzelnen Modi finden Sie in den folgenden Themen:  
  
-   [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL-&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [Projekteinstellungen &#40;Migrations&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [Projekteinstellungen&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [Projekteinstellungen &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [Projekteinstellungen &#40;Typzuordnung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
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
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping von DB2-und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Andernfalls können Sie die DB2-Datenbankobjekt Definitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von DB2-Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Zuordnung von DB2-und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
