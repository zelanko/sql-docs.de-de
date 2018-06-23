---
title: 'Aufgabe 2: Zuordnen von Excel-Spalten zu DQS-Domänen | Microsoft Docs'
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
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ff48d56555d3eca2bbcb961d753a47d8db38c69e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160819"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Aufgabe 2: Zuordnen von Excel-Spalten zu DQS-Domänen
    
1.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.  
  
2.  Klicken Sie auf **Durchsuchen**Option **Suppliers.xlsx**, und klicken Sie auf **öffnen**.  
  
3.  Wählen Sie **IncomingSuppliers$** für die **Arbeitsblatt**.  
  
4.  Ordnen Sie die Spalten an, wie in der folgenden Tabelle und im Screenshot dargestellt. Beim Erstellen von Zuordnungen für die **Status** Domäne, klicken Sie auf **spaltenzuordnung hinzufügen** auf der Symbolleiste direkt über der Liste befindet.  
  
    > [!TIP]  
    >  Sie verwenden nicht **Supplier ID** Spalte/Domäne, für die Bereinigung. Verwenden Sie die **Supplier ID** Domäne weiter unten in der abgleichsaktivität.  
  
    |Excel-Spalte|DQS-Domäne|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Adresszeile|Adresszeile|  
    |Ort|Ort|  
    |Status|Status|  
    |Country (klicken Sie auf **+ (spaltenzuordnung hinzufügen)** Symbolleiste, um eine Zeile hinzuzufügen.)|Country|  
    |Zip Code|PLZ|  
  
     ![Zuordnungen von Excel-Spalten zu Domänen](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Zuordnungen von Excel-Spalten zu Domänen")  
  
5.  Wie Sie die einzelnen Domänen innerhalb zugeordnet haben die **Address Validation** verbunddomäne Bereinigungsprozess automatisch die verbunddomäne teilnimmt. Klicken Sie auf **Verbunddomänen anzeigen/auswählen** Schaltfläche, um festzustellen, ob die **Address Validation** verbunddomäne automatisch ausgewählt ist, und klicken Sie dann auf **OK**.  
  
     ![Dialogfeld für anzeigen/auswählen Verbunddomänen](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "anzeigen/auswählen Verbunddomänen (Dialogfeld)")  
  
6.  Klicken Sie auf **Weiter** So wechseln Sie zu der **Bereinigen** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3: Bereinigung von Daten anhand der Wissensdatenbank „Suppliers“](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  