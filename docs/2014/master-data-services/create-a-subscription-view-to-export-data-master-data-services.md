---
title: Erstellen einer Abonnementsicht (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c4a2f747192b1cddefeac256d4470a2b345305de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65479945"
---
# <a name="create-a-subscription-view-master-data-services"></a>Erstellen einer Abonnementsicht (Master Data Services)
  Erstellen Sie eine Abonnementsicht, wenn Sie, erstellen Sie einen Überblick über Ihre Daten in möchten die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Datenbank für die Verwendung durch abonnementsysteme.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die entsprechende Berechtigung für den Zugriff auf den Funktionsbereich **Integrationsmanagement** verfügen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-create-a-subscription-view"></a>So erstellen Sie eine Abonnementsicht  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Integrationsmanagement**.  
  
2.  Klicken Sie auf der Menüleiste auf **Sichten erstellen**.  
  
3.  Auf der **Abonnementsichten** auf **Abonnementsicht hinzufügen**.  
  
4.  In der **Abonnementsicht erstellen** Bereich, in der **Name der Abonnementsicht** geben einen Namen für die Ansicht.  
  
5.  Wählen Sie aus der Liste **Modell** ein Modell aus.  
  
6.  Wählen Sie entweder die **Version** oder **Versionsflag** aus, und wählen Sie dann aus der entsprechenden Liste.  
  
    > [!TIP]  
    >  Erstellen Sie auf Grundlage eines Versionsflags eine Abonnementsicht. Wenn Sie eine Version sperren, können Sie das Flag einer geöffneten Version erneut zuweisen, ohne die Abonnementsicht zu aktualisieren.  
  
7.  Wählen Sie entweder die **Entität** oder **abgeleitete Hierarchie** aus, und wählen Sie dann aus der entsprechenden Liste.  
  
8.  Wählen Sie aus der Liste **Format** ein Format für die Abonnementsicht aus.  
  
9. Wenn Sie **Explizite Ebenen** oder **Abgeleitete Ebenen** aus der Liste **Format** ausgewählt haben, geben Sie die Anzahl der in die Sicht aufzunehmenden Hierarchieebenen ein.  
  
10. Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Siehe auch  
 [Exportieren von Daten &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Löschen einer Abonnementsicht &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md)   
 [Erstellen eines Versionsflags &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
