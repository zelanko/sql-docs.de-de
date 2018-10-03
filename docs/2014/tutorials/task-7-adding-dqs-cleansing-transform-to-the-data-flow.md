---
title: 'Aufgabe 7: Hinzufügen der DQS-Bereinigung Transformation dem Datenfluss | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 63af147462b9414bd85d0a301e908df4c774c7b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138196"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Aufgabe 7: Hinzufügen der Transformation für DQS-Bereinigung zum Datenfluss
  In dieser Aufgabe fügen Sie dem Datenfluss eine DQS-Bereinigungstransformation hinzu, um die Eingabelieferantendaten mithilfe von DQS zu bereinigen. Finden Sie unter **[DQS-Bereinigungstransformation](http://msdn.microsoft.com/library/ee677619.aspx)** für Weitere Informationen zur Transformation.  
  
1.  Mit der rechten Maustaste **DQS-Bereinigung** in die **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Cleanse Supplier Data**, und drücken Sie die **EINGABETASTE**.  
  
2.  Wählen Sie **Read Supplier Data from Excel File**; ziehen Sie den blauen Konnektor zu **Cleanse Supplier Data**. Die Komponenten sind jetzt verbunden.  
  
     ![Lieferantendaten lesen -> Lieferantendaten Bereinigen](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Lieferantendaten lesen -> Lieferantendaten bereinigen")  
  
3.  Doppelklicken Sie auf **Lieferantendaten Bereinigen**.  
  
4.  In der **DQS-Bereinigung Transformations-Editor**, klicken Sie auf **neu** neben der **Data Quality Services-Verbindungs-Manager-Dropdownliste**.  
  
5.  In der **DQS-Verbindungs-Manager-Bereinigung** (Dialogfeld), Typ **(local)** oder **Zeitraum** (.) für die Verbindung mit dem lokalen Server. In dieser Lektion wird davon ausgegangen, dass DQS auf einem lokalen Server installiert ist.  
  
6.  Klicken Sie auf **Verbindung testen** zum Testen der Verbindung mit DQS-Server.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
8.  Wählen Sie **Lieferanten** für die **Data Quality-Wissensdatenbank**.  
  
     ![DQS-Bereinigung Transformations-Editor – Lieferanten (KB)](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS-Bereinigung Transformations-Editor – Lieferanten (KB)")  
  
9. Wechseln Sie zu der **Zuordnung** auf der oberen Registerkarte.  
  
10. Von **verfügbare Eingabespalten**Option **Lieferantenname**, **ContactEmailAddress**, **Address Line**, **City**, **Zustand**, **Land**, und **Postleitzahl** durch Auswahl der Kontrollkästchen.  
  
     ![DQS-Bereinigung Transformations-Editor - Zuordnungen](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS-Bereinigung Transformations-Editor - Zuordnungen")  
  
11. Im unteren Bereich, ordnen Sie diese Spalten mithilfe der Dropdownlisten in der **Domäne** Spalte:  
  
    |Spalte|Domäne|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Adresszeile|Adresszeile|  
    |Ort|Ort|  
    |Status|Status|  
    |Country|Country|  
    |Zip Code|PLZ|  
  
12. Klicken Sie auf **OK** schließen die **DQS-Bereinigung Transformations-Editor** Dialogfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 8: Hinzufügen einer Transformation mit „Bedingtes Teilen“, um die Bereinigungsausgabe zu teilen](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
