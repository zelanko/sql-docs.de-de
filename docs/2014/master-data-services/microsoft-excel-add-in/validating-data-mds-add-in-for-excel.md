---
title: Überprüfen von Daten (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a01af53372a8be1fce6ffa2e4ee8d4cddce8d057
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135340"
---
# <a name="validating-data-mds-add-in-for-excel"></a>Überprüfen von Daten (MDS-Add-In für Excel)
  Beim Veröffentlichen von Daten werden in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]zwei Arten von Überprüfungen ausgeführt:  
  
-   Alle definierten Geschäftsregeln werden auf die Daten angewendet.  
  
-   Daten werden auf zulässige Attributwerte hin überprüft (z. B. die Anzahl der Zeichen oder der Typ der Daten).  
  
 Gültige Daten werden in jedem Fall im MDS-Repository veröffentlicht. Ungültige Daten werden hervorgehoben, und Details des Fehlers können in Statusspalten angezeigt werden.  
  
## <a name="when-validation-occurs"></a>Zeitpunkt der Überprüfungen  
 In der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], Überprüfung tritt auf, wenn Sie neue oder geänderte Daten veröffentlichen, oder Sie Geschäftsregeln manuell anwenden.  
  
 Wenn für die Geschäftsregeln ein Fehler auftritt, werden die Daten trotzdem im MDS-Repository veröffentlicht. Wenn die Überprüfung der Eingabe fehlschlägt, werden die Daten nicht im Repository veröffentlicht.  
  
## <a name="validation-statuses"></a>Überprüfungsstatus  
 Beim Veröffentlichen von Daten werden in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]sind die folgenden Überprüfungsstatus möglich.  
  
|Status|Description|  
|------------|-----------------|  
|Fehler|Für einen oder mehrere Werte in der Zeile ist bei der Überprüfung auf Grundlage der Geschäftsregeln, die von einem MDS-Administrator definiert wurden, ein Fehler aufgetreten.|  
|Nicht überprüft|Werte in der Zeile wurden noch nicht auf Grundlage der Geschäftsregeln überprüft.|  
|Success|Alle Werte in der Zeile haben die Überprüfung auf Grundlage der Geschäftsregeln bestanden.|  
  
## <a name="input-statuses"></a>Eingabestatus  
 Beim Veröffentlichen von Daten werden in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]sind die folgenden Eingabestatus möglich.  
  
|Status|Description|  
|------------|-----------------|  
|Fehler|Ein oder mehrere Werte in der Zeile erfüllen die Systemanforderungen nicht, z. B. Länge oder Datentyp. Der Wert wird im MDS-Repository nicht aktualisiert.|  
|Neue Zeile|Die Werte in der Zeile wurden noch nicht im MDS-Repository veröffentlicht.|  
|Schreibgeschützt|Der angemeldete Benutzer verfügt nur über die Leseberechtigung für einen oder mehrere Werte in der Zeile, und der Wert bzw. die Werte können nicht aktualisiert werden.|  
|Unverändert|Kein Wert in der Zeile wurde im Arbeitsblatt geändert. Dies bedeutet nicht, dass sich die Werte im Repository nicht geändert haben. Klicken Sie zum Abrufen der aktuellen Daten im Blatt in der Gruppe **Verbinden und Laden** auf **Laden oder Aktualisieren**.<br /><br /> Dies ist die Standardeinstellung für jede Zeile.|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Bestimmen Sie, welche Werte die definierten Geschäftsregeln nicht bestehen.|[Anwenden von Geschäftsregeln &#40;MDS-Add-in für Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)|  
|Zeigen Sie als Unterstützung beim Korrigieren von Überprüfungsfehlern alle Transaktionen an, die für ein Element ausgeführt wurden.|[Anzeigen aller Anmerkungen oder Transaktionen für ein Element &#40;MDS-Add-In für Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Veröffentlichen von Daten &#40;MDS-Add-in für Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
