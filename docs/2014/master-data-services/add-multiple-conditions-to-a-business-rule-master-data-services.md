---
title: Hinzufügen mehrerer Bedingungen zu einer Geschäftsregel (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ef62942c8dd9e2bf47522b4fa17f9ecfd3011561
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228538"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Hinzufügen mehrerer Bedingungen zu einer Geschäftsregel (Master Data Services)
  Sie können einer Geschäftsregel in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]mehrere **AND** - oder **OR** -Bedingungen hinzufügen, um eine komplexere Regel zu erstellen.  
  
> [!NOTE]  
>  Wenn Sie eine Geschäftsregel erstellen, die den **OR** -Operator verwendet, sollten Sie eine separate Regel für jede Bedingungsanweisung erstellen, die unabhängig ausgewertet werden kann. Sie können dann Regeln nach Bedarf ausschließen und so mehr Flexibilität und eine einfachere Problembehandlung bereitstellen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Eine Geschäftsregel muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>So fügen Sie einer Geschäftsregel mehrere Bedingungen hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Von der **Elementtyp** wählen Sie einen Typ des Elements.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf die Zeile für die Geschäftsregel, die Sie bearbeiten möchten.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. In der **Komponenten** Bereich, erweitern Sie die **logische Operatoren** Knoten.  
  
10. Klicken Sie auf **und** oder **OR** und ziehen Sie dann auf die **IF** des Bereichs **und** Bezeichnung.  
  
11. Erweitern Sie im Bereich **Komponenten** den Knoten **Bedingungen** .  
  
12. Klicken Sie auf eine Bedingung und ziehen Sie es auf **IF** Bereich, in der **und** oder **OR** Bezeichnung aus Schritt 10.  
  
13. In der **Attribute** Bereich, klicken Sie auf ein Attribut, und ziehen Sie dann auf die **Bedingung bearbeiten** des Bereichs **Attribut auswählen** Bezeichnung.  
  
14. In der **Bedingung bearbeiten** Bereich füllen Sie alle erforderlichen Felder.  
  
15. Klicken Sie im Bereich **Bedingung bearbeiten** auf **Element speichern**.  
  
16. Optional, um weitere Bedingungen hinzuzufügen der **Komponenten** ziehen Sie **und** oder **OR** auf **und** oder **OR**in die **IF** Bereich. Führen Sie dann die Schritte 13 bis 15 aus.  
  
    > [!TIP]  
    >  Um eine Bedingung zu löschen, klicken Sie auf den Namen der Bedingung und dann in der **Bedingung bearbeiten** Bereich, klicken Sie auf **elementlöschvorgang**.  
  
## <a name="see-also"></a>Siehe auch  
 [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Ändern des Namens einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Konfigurieren von Geschäftsregeln zum Senden von Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
