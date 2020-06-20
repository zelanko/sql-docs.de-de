---
title: Hinzufügen mehrerer Bedingungen zu einer Geschäftsregel (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf135e4c1f67a7187ec67284d52adcdb25c9bd27
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972280"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Hinzufügen mehrerer Bedingungen zu einer Geschäftsregel (Master Data Services)
  Sie können einer Geschäftsregel in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]mehrere **AND** - oder **OR** -Bedingungen hinzufügen, um eine komplexere Regel zu erstellen.  
  
> [!NOTE]  
>  Wenn Sie eine Geschäftsregel erstellen, die den **OR** -Operator verwendet, sollten Sie eine separate Regel für jede Bedingungsanweisung erstellen, die unabhängig ausgewertet werden kann. Sie können dann Regeln nach Bedarf ausschließen und so mehr Flexibilität und eine einfachere Problembehandlung bereitstellen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Eine Geschäftsregel muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>So fügen Sie einer Geschäftsregel mehrere Bedingungen hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie in der Liste **Elementtyp** einen Typ des Members aus.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf die Zeile für die Geschäftsregel, die Sie bearbeiten möchten.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. Erweitern Sie im Bereich **Komponenten** den Knoten **logische Operatoren** .  
  
10. Klicken Sie auf **and** oder **or** , und ziehen Sie es **auf die Bezeichnung** **und** .  
  
11. Erweitern Sie im Bereich **Komponenten** den Knoten **Bedingungen** .  
  
12. Klicken Sie auf eine Bedingung, und ziehen Sie Sie in den Bereich **if** , in die Bezeichnung **und** oder **oder** aus Schritt 10.  
  
13. Klicken Sie im Bereich **Attribute** auf ein Attribut, und ziehen Sie es im Bereich **Bedingung bearbeiten** auf die Bezeichnung **Attribut auswählen** .  
  
14. Vervollständigen Sie im Bereich **Bedingung bearbeiten** alle erforderlichen Felder.  
  
15. Klicken Sie im Bereich **Bedingung bearbeiten** auf **Element speichern**.  
  
16. Wenn Sie weitere Bedingungen hinzufügen möchten, ziehen Sie aus dem **Komponenten** Bereich **und** oder **oder** in beliebige **und** oder **oder** im **if** -Bereich. Führen Sie dann die Schritte 13 bis 15 aus.  
  
    > [!TIP]  
    >  Um eine Bedingung zu löschen, klicken Sie auf den Namen der Bedingung, und klicken Sie im Bereich **Bedingung bearbeiten** auf **Element löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Master Data Services von Geschäftsregeln &#40;&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Ändern Sie den Namen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Konfigurieren von Geschäftsregeln für das Senden von Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
