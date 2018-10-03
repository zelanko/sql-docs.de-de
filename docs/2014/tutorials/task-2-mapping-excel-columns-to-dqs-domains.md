---
title: 'Aufgabe 2: Zuordnen von Excel-Spalten zu DQS-Domänen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4af26cb52b8d30dbfad5fc5ab40dc732f8ce4dc2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135520"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Aufgabe 2: Zuordnen von Excel-Spalten zu DQS-Domänen
    
1.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.  
  
2.  Klicken Sie auf **Durchsuchen**Option **Suppliers.xlsx**, und klicken Sie auf **öffnen**.  
  
3.  Wählen Sie **IncomingSuppliers$** für die **Arbeitsblatt**.  
  
4.  Ordnen Sie die Spalten an, wie in der folgenden Tabelle und im Screenshot dargestellt. Beim Erstellen von Zuordnungen für die **Zustand** Domäne, klicken Sie auf **spaltenzuordnung hinzufügen** auf der Symbolleiste befindet sich direkt über der Liste.  
  
    > [!TIP]  
    >  Sie verwenden nicht **Supplier ID** Spalte/Domäne, für die Bereinigung. Verwenden Sie die **Supplier ID** Domäne weiter unten in der abgleichsaktivität.  
  
    |Excel-Spalte|DQS-Domäne|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Adresszeile|Adresszeile|  
    |Ort|Ort|  
    |Status|Status|  
    |Country (klicken Sie auf **+ (spaltenzuordnung hinzufügen)** Symbolleiste, um eine Zeile hinzufügen)|Country|  
    |Zip Code|PLZ|  
  
     ![Zuordnungen von Excel-Spalten zu Domänen](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Zuordnungen von Excel-Spalten zu Domänen")  
  
5.  Wie Sie, die die einzelnen Domänen innerhalb zugeordnet haben der **Address Validation** verbunddomäne, die verbunddomäne automatisch ist Teil des Bereinigungsprozesses. Klicken Sie auf **Verbunddomänen anzeigen/auswählen** Schaltfläche, um anzuzeigen, die die **Address Validation** verbunddomäne automatisch ausgewählt ist, und klicken Sie dann auf **OK**.  
  
     ![Anzeigen/auswählen Verbunddomänen Dialogfeld](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "Verbunddomänen-Dialogfeld anzeigen/auswählen")  
  
6.  Klicken Sie auf **Weiter** zum Wechseln der **Bereinigen** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3: Bereinigung von Daten anhand der Wissensdatenbank „Suppliers“](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
