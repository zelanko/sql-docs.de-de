---
title: 'Aufgabe 10: Konfigurieren der Verbunddomäne, um Reference Data Service zu verwenden. | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2a5d37578ac8336b67201161ef4de59baf90649c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056372"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Aufgabe 10: Konfigurieren der Verbunddomäne, um Reference Data Service zu verwenden
  In dieser Aufgabe Konfigurieren Sie die **Address Validation** verbunddomäne mit den **Melissa Data – Address Check** Dienst. Zur Laufzeit während der Bereinigungsaktivität gibt DQS die Werte der Domänen in der Domäne "Address Validation" zur Bereinigung an den Dienst weiter. Finden Sie unter [Zuordnung Domäne/Verbunddomäne an Verweisdaten](http://msdn.microsoft.com/library/hh213030.aspx) Weitere Details.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Suppliers (Domain Management)** unter **zuletzt verwendete Wissensdatenbank** zum Starten der **Domänenverwaltung**Seite.  
  
2.  Wählen Sie die **Address Validation** verbunddomäne in der **Liste der Domänen**.  
  
3.  Wechseln Sie im rechten Bereich in der **Verweisdaten** Registerkarte.  
  
     ![Verweisen auf die Registerkarte "Daten"](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "verweisen auf die Registerkarte \"Daten\"")  
  
4.  Klicken Sie auf **Durchsuchen** auf der Symbolleiste.  
  
5.  Auf der **Data Provider Onlinekatalog der Reference** wählen Sie im Dialogfeld **Kontrollkästchen** neben **Melissa Data – Address Check**.  
  
     ![Wählen Sie Melissa Data – Adresse](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Melissa Data – Adresse wählen")  
  
6.  Im rechten Bereich in der **Schema** ordnen Sie **Address Line** Domäne für die **Address Line (M)** Schemaelement mithilfe der Dropdown-Liste.  
  
     ![Zuordnen von RDS-Schemaelements Domäne](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "RDS-Schemaelements-Domäne zuordnen")  
  
7.  Klicken Sie auf **Schemaeintrag hinzufügen (+)** auf der Symbolleiste in der Liste einen Eintrag zu erstellen.  
  
     ![Schema Eintrag Symbolleisten-Schaltfläche "hinzufügen"](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Schema Eintrag Symbolleisten-Schaltfläche \"hinzufügen\"")  
  
8.  Ordnen Sie die folgenden DQS-Domänen mit den Dropdownlisten zu, wie in der folgenden Abbildung gezeigt.  
  
     ![Zuordnen von RDS-Schemaelementen zu Domänen](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Zuordnen von RDS-Schemaelementen zu Domänen")  
  
9. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 11: Veröffentlichen der Wissensdatenbank](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  