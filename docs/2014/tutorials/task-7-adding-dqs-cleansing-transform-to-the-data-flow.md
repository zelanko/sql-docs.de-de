---
title: 'Aufgabe 7: Hinzufügen der Transformation für die DQS-Bereinigung zum Datenfluss | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0978452104eb9a55d49dfa9f851ef7578489db26
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85006484"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Aufgabe 7: Hinzufügen der Transformation für DQS-Bereinigung zum Datenfluss
  In dieser Aufgabe fügen Sie dem Datenfluss eine DQS-Bereinigungstransformation hinzu, um die Eingabelieferantendaten mithilfe von DQS zu bereinigen. Weitere Informationen zur Transformation finden Sie unter **[DQS](https://msdn.microsoft.com/library/ee677619.aspx)** -Bereinigungs Transformation.  
  
1.  Klicken Sie **mit der rechten** Maustaste auf **DQS-Bereinigung** , und klicken Sie auf **Umbenennen**. Geben Sie Hersteller **Daten**bereinigen ein, und drücken **Sie Eingabe**Taste.  
  
2.  Wählen Sie **Lieferantendaten aus Excel-Datei lesen aus**. Ziehen Sie den blauen Connector, um **Lieferantendaten**zu bereinigen. Die Komponenten sind jetzt verbunden.  
  
     ![Lesen von Lieferantendaten > Bereinigen der Lieferantendaten](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Lieferantendaten lesen -> Lieferantendaten bereinigen")  
  
3.  Doppelklicken Sie auf **Lieferantendaten**bereinigen.  
  
4.  Klicken Sie im Transformations-Editor für die **DQS-Bereinigung**neben der **Dropdown Liste Data Quality-Verbindungs-Manager**auf **neu** .  
  
5.  Geben Sie im Dialogfeld **Verbindungs-Manager für DQS-Bereinigung** **(local)** oder **Period** (.) ein, um eine Verbindung mit dem lokalen Server herzustellen. In dieser Lektion wird davon ausgegangen, dass DQS auf einem lokalen Server installiert ist.  
  
6.  Klicken Sie auf **Verbindung testen** , um die Verbindung mit dem DQS-Server zu testen.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
8.  Wählen Sie **Suppliers** für die **Data Quality-Wissensdatenbank**aus.  
  
     ![Transformations-Editor für die DQS-Bereinigung – Lieferanten (KB)](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "Transformations-Editor für die DQS-Bereinigung – Lieferanten (KB)")  
  
9. Wechseln Sie oben zur Registerkarte **Zuordnung** .  
  
10. Wählen Sie unter **Verfügbare Eingabe Spalten**die Option **Lieferanten Name**, **contactemailaddress**, **Adresszeile**, **Ort**, **Bundes** **Land, Land**und **Postleitzahl** aus, indem Sie die Kontrollkästchen aktivieren.  
  
     ![Transformations-Editor für die DQS-Bereinigung – Zuordnungen](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "Transformations-Editor für die DQS-Bereinigung – Zuordnungen")  
  
11. Ordnen Sie diese Spalten im unteren Bereich mithilfe von Dropdown Listen in der Spalte **Domäne** zu:  
  
    |Column|Domain|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Kontakt-E-Mail|  
    |Adresszeile|Adresszeile|  
    |City|City|  
    |State|State|  
    |Land|Land|  
    |Zip Code|Zip|  
  
12. Klicken Sie zum Schließen des Dialog Felds **Transformations-Editor für DQS-Bereinigung** auf **OK** .  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 8: Hinzufügen der Transformation „Bedingtes Teilen“ zur Teilung der Bereinigungsausgabe](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
