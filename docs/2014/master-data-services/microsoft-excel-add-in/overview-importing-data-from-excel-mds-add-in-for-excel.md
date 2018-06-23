---
title: Veröffentlichen von Daten (MDS-Add-in für Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 39acbad0925e8dfc250fcd4cc3913dbaf0ff0771
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060520"
---
# <a name="publishing-data-mds-add-in-for-excel"></a>Veröffentlichen von Daten (MDS-Add-In für Excel)
  Veröffentlichen Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]im MDS-Repository Daten, wenn Sie diese für andere Benutzer freigeben möchten. Sobald die Daten veröffentlicht werden, stehen sie anderen Benutzern des Add-Ins zum Herunterladen zur Verfügung.  
  
 Wenn Sie Daten veröffentlichen, werden alle Daten, die Sie hinzugefügt oder aktualisiert haben, im MDS-Repository veröffentlicht. Gelöschte Daten werden nicht veröffentlicht. Sie müssen Daten separat löschen. Weitere Informationen finden Sie unter [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Die Veröffentlichung kann nicht zum Erstellen einer neuen Entität verwendet werden. Weitere Informationen zum Erstellen von Entitäten finden Sie unter [Erstellen einer Entität &#40;MDS-Add-In für Excel&#41;](create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Wenn mehrere Benutzer gleichzeitig veröffentlichen  
 Mehrere Benutzer können Updates zu den gleichen Daten veröffentlichen. Sobald jeder Benutzer veröffentlicht hat, wird das Update in der Datenbank gespeichert. Dies bedeutet, dass ein Benutzer, der nicht mit den zuletzt aktualisierten Daten gearbeitet hat, immer noch den Wert ändern kann, wenn er oder sie veröffentlicht.  
  
 Nur die Updates, die Sie vornehmen, werden in der Datenbank veröffentlicht. Alle veraltete Daten im Arbeitsblatt werden nicht veröffentlicht.  
  
## <a name="transactions-and-annotations"></a>Transaktionen und Anmerkungen  
 Jede veröffentlichte Änderung wird als Transaktion gespeichert. Wenn Sie möchten, können Sie einer Transaktion Anmerkungen (Kommentare) hinzufügen, um zu erklären, warum Sie die Änderung vorgenommen haben.  
  
-   Sie können keine Löschungen kommentieren, obwohl Löschungen als Transaktionen gespeichert werden, die von einem Administrator umgekehrt werden können.  
  
-   Wenn Sie ändern die **Code** Wert für ein Element, wird er nicht als Transaktion aufgezeichnet, und alle vorherige Transaktionen für das Element nicht verfügbar ist.  
  
-   Sie können Transaktionen anzeigen, die von anderen Benutzern an einem Element vorgenommen wurden. Sie können auch alle Transaktionen anzeigen, die Sie an einem Element vorgenommen haben, auch wenn Sie nicht mehr über die Berechtigung für bestimmte Attribute verfügen.  
  
 Sie können alle an einem Element vorgenommenen Transaktionen anzeigen. Weitere Informationen finden Sie unter [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Wenn Sie eine Anmerkung von mehr als 500 Zeichen eingeben, wird die Anmerkung automatisch abgeschnitten.  
  
## <a name="business-rule-and-other-validation"></a>Geschäftsregel und andere Überprüfung  
 Wenn Sie Daten veröffentlichen, wird eine Überprüfung ausgeführt, um sicherzustellen, dass die Daten exakt sind, bevor sie dem MDS-Repository hinzugefügt werden. Wenn die Daten die angegebenen Kriterien nicht erfüllen, werden sie nicht im Repository veröffentlicht. Weitere Informationen finden Sie unter [Überprüfen von Daten &#40;MDS-Add-In für Excel&#41;](validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Veröffentlichen Sie Daten vom aktiven Arbeitsblatt zurück zum MDS-Repository.|[Veröffentlichen von Daten aus Excel nach MDS &#40;MDS-Add-in für Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Löschen Sie eine Zeile aus dem MDS-Repository und vom Arbeitsblatt zur gleichen Zeit.|[Löschen einer Zeile &#40;MDS-Add-in für Excel&#41;](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Aktualisieren von Daten &#40;MDS-Add-In für Excel&#41;](refreshing-data-mds-add-in-for-excel.md)  
  
-   [Master Data Services-Add-in für Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  