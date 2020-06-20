---
title: 'Aufgabe 10: Konfigurieren der Verbund Domäne für die Verwendung von Reference Data Service | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: dd1727ffaa24edf12ed7ad8a5fb4f55f4910855e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064821"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Aufgabe 10: Konfigurieren der Verbunddomäne für die Verwendung von Verweisdatendiensten
  In dieser Aufgabe konfigurieren Sie die Verbund Domäne für die **Adressvalidierung** so, dass Sie den Dienst **Melissa-Daten Adressüberprüfung** verwendet. Zur Laufzeit während der Bereinigungsaktivität gibt DQS die Werte der Domänen in der Domäne "Address Validation" zur Bereinigung an den Dienst weiter. Weitere Informationen finden [Sie unterzuordnen einer Domäne/Verbund Domäne zu Verweis Daten](https://msdn.microsoft.com/library/hh213030.aspx) .  
  
1.  Klicken Sie auf der Hauptseite des **DQS-Clients**unter **zuletzt verwendete Wissensdatenbanken** auf **Suppliers (Domänen Verwaltung)** , um die Seite **Domänen Verwaltung** zu starten.  
  
2.  Wählen Sie die Verbund Domäne **Address Validation** in der **Liste der Domänen aus**.  
  
3.  Wechseln Sie im rechten Bereich zur Registerkarte **Verweis Daten** .  
  
     ![Verweisdaten (Registerkarte)](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Verweisdaten (Registerkarte)")  
  
4.  Klicken Sie auf der Symbolleiste auf **Durchsuchen** .  
  
5.  Aktivieren Sie im Dialogfeld **Online Katalog der Verweis Datenanbieter** das **Kontrollkästchen** neben **Melissa Data-Address Check**.  
  
     ![Auswählen von "Melissa Data – Adresse"](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Auswählen von "Melissa Data – Adresse"")  
  
6.  Ordnen Sie im rechten Bereich im Abschnitt **Schema** **der Adresszeile** **(M)** das Schema Element mithilfe der Dropdown Liste zu.  
  
     ![Zuordnen des RDS-Schemaelements zur Domäne](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Zuordnen des RDS-Schemaelements zur Domäne")  
  
7.  Klicken Sie in der Symbolleiste auf die Schaltfläche **Schema Eintrag hinzufügen (+)** , um einen Eintrag in der Liste zu erstellen.  
  
     ![Schemaeintrag hinzufügen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Schemaeintrag hinzufügen (Symbolleistenschaltfläche)")  
  
8.  Ordnen Sie die folgenden DQS-Domänen mit den Dropdownlisten zu, wie in der folgenden Abbildung gezeigt.  
  
     ![Zuordnen von RDS-Schemaelementen zu Domänen](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Zuordnen von RDS-Schemaelementen zu Domänen")  
  
9. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 11: Veröffentlichen der Wissensdatenbank](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
