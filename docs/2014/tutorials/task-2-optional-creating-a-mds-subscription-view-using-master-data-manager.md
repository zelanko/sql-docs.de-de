---
title: 'Aufgabe 2 (optional): Erstellen einer MDS-Abonnementsicht mithilfe von Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e6cbed42d059714dde1c82dbb50edf8ccc1dd65b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484724"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Aufgabe 2 (optional): Erstellen einer MDS-Abonnementsicht mithilfe des Master Data Manager
  In dieser Aufgabe erstellen Sie eine Abonnementsicht, um verfügbar zu machen die **Lieferanten** Entität in der **Lieferanten** Modelle für andere Anwendungen. Sie verwenden diese Sicht nicht in der aktuellen Version des Lernprogramms.  
  
1.  Wechseln Sie zur Hauptseite des **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)) durch Klicken auf **SQL Server 2012 Master Data Services** oben.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Klicken Sie auf **Sichten erstellen** in der Menüleiste.  
  
     ![Hinzufügen einer neuen Abonnement anzeigen Schaltfläche](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "eine neues Abonnement anzeigen-Schaltfläche \"hinzufügen\"")  
  
4.  Klicken Sie auf **+ (Plus)** Symbol auf der Symbolleiste können Sie eine Abonnementsicht zu erstellen.  
  
5.  In der **Abonnementsicht erstellen** im Bereich **Lieferanten** für **Name der Abonnementsicht**.  
  
6.  Wählen Sie **Lieferanten** für **Modell**.  
  
7.  Wählen Sie **VERSION_1** für **Version**.  
  
8.  Wählen Sie **Lieferanten** für **Entität**.  
  
9. Wählen Sie **Blattelemente** für **Format**.  
  
     ![Speichern Sie die Schaltfläche "Abonnement-Ansicht"](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Abonnement anzeigen-Schaltfläche \"Speichern\"")  
  
10. Klicken Sie auf **speichern** auf der Symbolleiste auf die Abonnementsicht zu speichern. Diese Aktion erstellt eine Sicht in SQL Server mit dem Namen **Lieferanten**. Sie können dies mit SQL Server Management Studio (SSMS) überprüfen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3 &#40;Optional&#41;: Überprüfung der Abonnementsichten](task-3-optional-reviewing-the-subscription-views.md)  
  
  
