---
title: Veröffentlichen von Daten (MDS-Add-in für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: dd5046c9a307f498ffb585c99cba8044c7b18b3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479030"
---
# <a name="publishing-data-mds-add-in-for-excel"></a>Veröffentlichen von Daten (MDS-Add-In für Excel)
  Veröffentlichen Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]im MDS-Repository Daten, wenn Sie diese für andere Benutzer freigeben möchten. Sobald die Daten veröffentlicht werden, stehen sie anderen Benutzern des Add-Ins zum Herunterladen zur Verfügung.  
  
 Wenn Sie Daten veröffentlichen, werden alle Daten, die Sie hinzugefügt oder aktualisiert haben, im MDS-Repository veröffentlicht. Gelöschte Daten werden nicht veröffentlicht. Sie müssen Daten separat löschen. Weitere Informationen finden Sie unter [Löschen einer Zeile &#40;MDS-Add-In für Excel&#41;](delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Die Veröffentlichung kann nicht zum Erstellen einer neuen Entität verwendet werden. Weitere Informationen zum Erstellen von Entitäten finden Sie unter [Erstellen einer Entität &#40;MDS-Add-In für Excel&#41;](create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Wenn mehrere Benutzer gleichzeitig veröffentlichen  
 Mehrere Benutzer können Updates zu den gleichen Daten veröffentlichen. Sobald jeder Benutzer veröffentlicht hat, wird das Update in der Datenbank gespeichert. Dies bedeutet, dass ein Benutzer, der nicht mit den zuletzt aktualisierten Daten gearbeitet hat, immer noch den Wert ändern kann, wenn er oder sie veröffentlicht.  
  
 Nur die Updates, die Sie vornehmen, werden in der Datenbank veröffentlicht. Alle veraltete Daten im Arbeitsblatt werden nicht veröffentlicht.  
  
## <a name="transactions-and-annotations"></a>Transaktionen und Anmerkungen  
 Jede veröffentlichte Änderung wird als Transaktion gespeichert. Wenn Sie möchten, können Sie einer Transaktion Anmerkungen (Kommentare) hinzufügen, um zu erklären, warum Sie die Änderung vorgenommen haben.  
  
-   Sie können keine Löschungen kommentieren, obwohl Löschungen als Transaktionen gespeichert werden, die von einem Administrator umgekehrt werden können.  
  
-   Wenn Sie den **Codewert** für ein Element ändern, wird er nicht als Transaktion aufgezeichnet, und alle vorherigen Transaktionen für den Member sind nicht verfügbar.  
  
-   Sie können Transaktionen anzeigen, die von anderen Benutzern an einem Element vorgenommen wurden. Sie können auch alle Transaktionen anzeigen, die Sie an einem Element vorgenommen haben, auch wenn Sie nicht mehr über die Berechtigung für bestimmte Attribute verfügen.  
  
 Sie können alle an einem Element vorgenommenen Transaktionen anzeigen. Weitere Informationen finden Sie unter [Anzeigen aller Anmerkungen oder Transaktionen für ein Element &#40;MDS-Add-In für Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Wenn Sie eine Anmerkung von mehr als 500 Zeichen eingeben, wird die Anmerkung automatisch abgeschnitten.  
  
## <a name="business-rule-and-other-validation"></a>Geschäftsregel und andere Überprüfung  
 Wenn Sie Daten veröffentlichen, wird eine Überprüfung ausgeführt, um sicherzustellen, dass die Daten richtig sind, bevor sie dem MDS-Repository hinzugefügt werden. Wenn die Daten die angegebenen Kriterien nicht erfüllen, werden sie nicht im Repository veröffentlicht. Weitere Informationen finden Sie unter [Überprüfen von Daten &#40;MDS-Add-In für Excel&#41;](validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Veröffentlichen Sie Daten vom aktiven Arbeitsblatt zurück zum MDS-Repository.|[Daten aus Excel in MDS &#40;MDS-Add-in für Excel veröffentlichen&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Löschen Sie eine Zeile aus dem MDS-Repository und vom Arbeitsblatt zur gleichen Zeit.|[Zeilen &#40;MDS-Add-in für Excel löschen&#41;](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Aktualisieren von Daten &#40;MDS-Add-in für Excel&#41;](refreshing-data-mds-add-in-for-excel.md)  
  
-   [Master Data Services-Add-In für Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
