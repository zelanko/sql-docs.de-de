---
title: Initiieren von Aktionen auf der Grundlage von Attributwertänderungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 41aaf404aff55e4b88a73e693e34e6afa84f0a96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151084"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a>Initiieren von Aktionen auf der Grundlage von Attributwertänderungen (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Geschäftsregel, um Aktionen auf der Grundlage von Änderungen an Attributwerten zu initiieren. Wenn beispielsweise ein bestimmter Attributwert geändert wird, können Sie einen Wert ändern, eine Benachrichtigung, senden oder einen externen Workflow starten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Die Attribute müssen in einer Änderungsnachverfolgungsgruppe sein. Weitere Informationen finden Sie unter [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a>So erstellen Sie eine Geschäftsregel, um Aktionen auf der Grundlage von Änderungen an Attributwerten zu initiieren  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie aus der Liste **Elementtyp** einen Typ des Elements aus, auf das die Geschäftsregel angewendet werden soll.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf **Geschäftsregel hinzufügen**.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. Erweitern Sie im Bereich **Komponenten** den Knoten **Bedingungen** .  
  
10. Ziehen Sie unter dem Knoten **Wertvergleich** **Wurde geändert in** zur Bezeichnung **Bedingungen** des Bereichs **IF** .  
  
11. In der **Attribute** Bereich, klicken Sie auf ein Attribut, und ziehen Sie dann auf die **Bedingung bearbeiten** des Bereichs **Attribut auswählen** Bezeichnung. Dieses Attribut hat keine Auswirkungen auf die Regel; wählen Sie deshalb jedes verfügbares Attribut aus.  
  
12. Geben Sie im Bereich **Bedingung bearbeiten** im Feld **Änderungsnachverfolgungsgruppe** die Nummer der Änderungsnachverfolgungsgruppe ein, die Sie als Teil der erforderlichen Komponenten zugewiesen haben.  
  
13. Klicken Sie im Bereich **Bedingung bearbeiten** auf **Element speichern**.  
  
14. Erweitern Sie im Bereich **Komponenten** den Knoten **Aktionen** .  
  
15. Klicken Sie auf eine Aktion, und ziehen Sie sie auf die Bezeichnung **Aktion** des Bereichs **THEN** .  
  
16. Klicken Sie im Bereich **Attribute** auf ein Attribut, und ziehen Sie es im Bereich **Aktion bearbeiten** auf die Bezeichnung **Attribut auswählen** .  
  
17. Vervollständigen Sie im Bereich **Aktion bearbeiten** alle Pflichtfelder.  
  
18. Klicken Sie im Bereich **Aktion bearbeiten** auf **Element speichern**.  
  
19. Klicken Sie auf **Zurück**.  
  
20. Optional können Sie auf der Seite **Verwaltung von Geschäftsregeln** für die Zeile, die die Geschäftsregel enthält, auf eine Zelle in den Spalten **Name**, **Beschreibung**oder **Benachrichtigung** doppelklicken, um den Wert zu aktualisieren.  
  
    > [!NOTE]  
    >  Benachrichtigungen werden nur für Regeln gesendet, die eine Überprüfungsaktion einschließen.  
  
21. Klicken Sie auf **Geschäftsregeln veröffentlichen**.  
  
22. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Status der Regel ändert sich zu **Aktiv**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Führen Sie zum Anwenden von Geschäftsregeln auf Daten eine der folgenden Prozeduren aus:  
  
    -   [Überprüfen von bestimmten Elementen auf Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)   
 [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
