---
title: 'Aufgabe 6: Hinzufügen von Excel-Quelle zum Datenfluss | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1cde5dc49851e7d8c808d4a6273f4d4caf6603e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163249"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Aufgabe 6: Hinzufügen der Excel-Quelle zum Datenfluss
  In dieser Aufgabe fügen Sie dem Datenfluss eine Excel-Quelle hinzu, um Lieferantendaten aus der Excel-Quelldatei zu lesen. Die Excel-Quelle extrahiert Daten aus Arbeitsblättern oder Bereichen in Microsoft Excel-Arbeitsmappen. Finden Sie unter [Excel-Quelle](http://msdn.microsoft.com/library/ms141683.aspx) Weitere Informationen.  
  
1.  Drag & Drop **Excel-Quelle** aus **anderen Quellen** in **SSIS-Toolbox** auf die **Datenfluss** Registerkarte.  
  
2.  Mit der rechten Maustaste auf **Excel-Quelle** in der **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**.  
  
3.  Typ **Read Supplier Data from Excel File** , und drücken Sie **EINGABETASTE**.  
  
4.  Doppelklicken Sie auf **Read Supplier Data from Excel File** zum Starten der **Quellen-Editor für Excel** (Dialogfeld).  
  
5.  In der **Quellen-Editor für Excel** (Dialogfeld), klicken Sie auf **neu** zum Erstellen einer Excel-Verbindung.  
  
6.  In der **Excel-Verbindungs-Manager** (Dialogfeld), klicken Sie auf **Durchsuchen**, und wählen Sie dann die **Suppliers.xls** in der Datei die **EIM Tutorial** Ordner . Überprüfen Sie, ob **Microsoft Excel 97-2003** ausgewählt ist, der **Excel-Version** Feld, und klicken Sie dann auf **OK**.  
  
     ![Excel-Verbindungs-Manager-Dialogfeld](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel-Verbindungs-Manager (Dialogfeld)")  
  
7.  In der **Quellen-Editor für Excel** wählen Sie im Dialogfeld **IncomingSuppliers$** in der **Name der Excel-Tabelle** Listenfeld.  
  
     ![Name der Excel-Tabelle – eingehende Lieferanten$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name der Excel-Tabelle – eingehende Lieferanten$")  
  
8.  Klicken Sie auf **Vorschau** auf die Daten in Excel-Datei in der Vorschau anzeigen.  
  
9. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
10. Drag & Drop **DQS-Bereinigung** Transformation **Weitere Transformationen** auf die **SSIS-Toolbox** auf die **Datenfluss** Registerkarte  **Supplier Data from Excel File lesen**. Die DQS-Bereinigungstransformation verwendet Data Quality Services (DQS), um die Daten zu korrigieren, indem sie genehmigte Regeln in der Wissensdatenbank anwendet. Diese Transformation erstellt zur Laufzeit ein DQS-Bereinigungsprojekt auf dem DQS-Server. Finden Sie unter [DQS-Bereinigungstransformation](http://msdn.microsoft.com/library/ee677619.aspx) Weitere Informationen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 7: Hinzufügen der Transformation für DQS-Bereinigung zum Datenfluss](../integration-services/data-flow/data-flow.md)  
  
  