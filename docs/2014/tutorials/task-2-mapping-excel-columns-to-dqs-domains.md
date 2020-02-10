---
title: 'Aufgabe 2: Zuordnung von Excel-Spalten zu DQS-Domänen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d45e06dcd3e67af3abbc6b356d44877e40f46b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484705"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Aufgabe 2: Zuordnen von Excel-Spalten zu DQS-Domänen
    
1.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.  
  
2.  Klicken Sie auf **Durchsuchen**, wählen Sie **Suppliers. xlsx**, und klicken Sie auf **Öffnen**.  
  
3.  Wählen Sie **incomingsuppliers $** für das **Arbeitsblatt**aus.  
  
4.  Ordnen Sie die Spalten an, wie in der folgenden Tabelle und im Screenshot dargestellt. Wenn Sie Zuordnungen für die **Zustands** Domäne erstellen, klicken Sie auf die Schaltfläche **Spalten Zuordnung hinzufügen** auf der Symbolleiste, die sich direkt über der Liste befindet.  
  
    > [!TIP]  
    >  Sie verwenden die Spalte/Domäne der **Lieferanten-ID** nicht für die Bereinigung. Sie verwenden die **Lieferanten-ID** -Domäne später in der abgleichsaktivität.  
  
    |Excel-Spalte|DQS-Domäne|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Kontakt-E-Mail|  
    |Adresszeile|Adresszeile|  
    |City|City|  
    |State|State|  
    |Country (Klicken Sie auf **+ (Spalten Zuordnung hinzufügen)** Symbolleiste, um eine Zeile hinzuzufügen)|Country|  
    |Zip Code|Zip|  
  
     ![Zuordnen von Excel-Spalten zu Domänen](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Zuordnen von Excel-Spalten zu Domänen")  
  
5.  Wenn Sie alle einzelnen Domänen innerhalb der Verbund Domäne der **Adressvalidierung** zugeordnet haben, wird die Verbund Domäne automatisch an dem Bereinigungs Prozess beteiligt. Klicken Sie auf die Schaltfläche **Verbund Domänen anzeigen/auswählen** , um anzuzeigen, dass die Verbund Domäne für die **Adressvalidierung** automatisch ausgewählt ist, **und klicken Sie dann auf**  
  
     ![Verbunddomänen anzeigen/auswählen (Dialogfeld)](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "Verbunddomänen anzeigen/auswählen (Dialogfeld)")  
  
6.  Klicken Sie auf **weiter** , um **zur Seite** bereinigen zu wechseln.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3: Bereinigung von Daten anhand der Wissensdatenbank 'Suppliers'](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
