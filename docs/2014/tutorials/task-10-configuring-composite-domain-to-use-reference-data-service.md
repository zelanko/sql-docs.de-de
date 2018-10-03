---
title: 'Aufgabe 10: Konfigurieren der Verbunddomäne, um Reference Data Service zu verwenden. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4e4a8ef8c3b9d60040d6d9b5fcbff145a600cd88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167680"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Aufgabe 10: Konfigurieren der Verbunddomäne, um Reference Data Service zu verwenden
  In dieser Aufgabe Konfigurieren Sie die **Address Validation** verbunddomäne mit den **Melissa Data – Address Check** Service. Zur Laufzeit während der Bereinigungsaktivität gibt DQS die Werte der Domänen in der Domäne "Address Validation" zur Bereinigung an den Dienst weiter. Finden Sie unter [Zuordnung Domäne/Verbunddomäne an Verweisdaten](http://msdn.microsoft.com/library/hh213030.aspx) Weitere Details.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Suppliers (Domain Management)** unter **zuletzt verwendete Wissensdatenbank** zum Starten der **Domänenverwaltung**Seite.  
  
2.  Wählen Sie die **Address Validation** verbunddomäne in der **Liste der Domänen**.  
  
3.  Wechseln Sie im rechten Bereich die **Verweisdaten** Registerkarte.  
  
     ![Verweisen auf die Registerkarte "Daten"](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "verweisen auf die Registerkarte \"Daten\"")  
  
4.  Klicken Sie auf **Durchsuchen** auf der Symbolleiste.  
  
5.  Auf der **Online Reference Data Providers Catalog** wählen Sie im Dialogfeld **Kontrollkästchen** neben **Melissa Data – Address Check**.  
  
     ![Wählen Sie Melissa Data – Adresse](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Melissa Data – Adresse auswählen")  
  
6.  Im rechten Bereich in der **Schema** ordnen **Address Line** Domäne die **Address Line (M)** Schemaelement mithilfe der Dropdown-Liste.  
  
     ![Zuordnen von RDS-Schemaelements zu Domäne](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "RDS-Schemaelements-Domäne zuordnen")  
  
7.  Klicken Sie auf **Schemaeintrag hinzufügen (+)** auf der Symbolleiste, um einen Eintrag in der Liste zu erstellen.  
  
     ![Hinzufügen von Schemas Eintrag Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Schema Eintrag Symbolleisten-Schaltfläche \"hinzufügen\"")  
  
8.  Ordnen Sie die folgenden DQS-Domänen mit den Dropdownlisten zu, wie in der folgenden Abbildung gezeigt.  
  
     ![Zuordnen von RDS-Schemaelementen zu Domänen](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "RDS-Schemaelementen zu Domänen zuordnen")  
  
9. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 11: Veröffentlichen der Wissensdatenbank](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
