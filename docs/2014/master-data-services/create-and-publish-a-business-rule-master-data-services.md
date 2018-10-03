---
title: Erstellen und Veröffentlichen einer Geschäftsregel (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: dade621e2dc095ee08a803351f6692d4c4a5cc34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227020"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a>Erstellen und Veröffentlichen einer Geschäftsregel (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Geschäftsregel, um die Genauigkeit der Masterdaten sicherzustellen. Nachdem Sie eine Regel erstellt haben, müssen Sie diese veröffentlichen, damit Sie sie auf Daten anwenden können.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-and-publish-a-business-rule"></a>So erstellen und veröffentlichen Sie eine Geschäftsregel  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie aus der Liste **Elementtyp** einen Typ des Elements aus, auf das die Geschäftsregel angewendet werden soll.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf **Geschäftsregel hinzufügen**.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. Erweitern Sie im Bereich **Komponenten** den Knoten **Bedingungen** .  
  
10. Klicken Sie auf eine Bedingung und ziehen Sie dann auf die **IF** des Bereichs **Bedingungen** Bezeichnung.  
  
    > [!TIP]  
    >  Sie können Elemente aus Ihrer Geschäftsregel löschen, indem Sie mit der rechten Maustaste und auswählen **löschen**.  
  
11. In der **Attribute** Bereich, klicken Sie auf ein Attribut, und ziehen Sie dann auf die **Bedingung bearbeiten** des Bereichs **Attribut auswählen** Bezeichnung.  
  
12. In der **Bedingung bearbeiten** Bereich füllen Sie alle erforderlichen Felder.  
  
13. Klicken Sie im Bereich **Bedingung bearbeiten** auf **Element speichern**.  
  
14. Erweitern Sie im Bereich **Komponenten** den Knoten **Aktionen** .  
  
15. Klicken Sie auf eine Aktion, und ziehen Sie sie auf die Bezeichnung **Aktion** des Bereichs **THEN** .  
  
16. Klicken Sie im Bereich **Attribute** auf ein Attribut, und ziehen Sie es im Bereich **Aktion bearbeiten** auf die Bezeichnung **Attribut auswählen** .  
  
17. Vervollständigen Sie im Bereich **Aktion bearbeiten** alle Pflichtfelder.  
  
18. Klicken Sie im Bereich **Aktion bearbeiten** auf **Element speichern**.  
  
19. Fügen Sie der Regel option mehrere Bedingungen hinzu. Weitere Informationen finden Sie unter [Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).  
  
20. Klicken Sie auf **Zurück**.  
  
21. Optional können Sie auf der Seite **Verwaltung von Geschäftsregeln** für die Zeile, die die Geschäftsregel enthält, auf eine Zelle in den Spalten **Name**, **Beschreibung**oder **Benachrichtigung** doppelklicken, um den Wert zu aktualisieren.  
  
    > [!NOTE]  
    >  Benachrichtigungen werden nur für Regeln gesendet, die eine Überprüfungsaktion einschließen.  
  
22. Klicken Sie auf **Geschäftsregeln veröffentlichen**.  
  
23. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Status der Regel ändert sich zu **Aktiv**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Führen Sie zum Anwenden von Geschäftsregeln auf Daten eine der folgenden Prozeduren aus:  
  
    -   [Überprüfen von bestimmten Elementen auf Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Geschäftsregeln zum Senden von Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)   
 [Ändern des Namens einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Hinzufügen mehrerer Bedingungen zu einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
