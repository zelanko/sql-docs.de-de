---
title: 'Aufgabe 2 (optional): Erstellen einer MDS-Abonnement Sicht mithilfe Master Data Manager | Microsoft-Dokumentation'
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
ms.openlocfilehash: cc923792adc3fefb5ebaab9e225169648394c71f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484710"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Aufgabe 2 (optional): Erstellen einer MDS-Abonnementsicht mithilfe des Master Data Manager
  In dieser Aufgabe erstellen Sie eine Abonnement Sicht, um die Entität **Supplier** im **Lieferanten** Modell für andere Anwendungen verfügbar zu machen. Sie verwenden diese Sicht nicht in der aktuellen Version des Lernprogramms.  
  
1.  Wechseln Sie zur Hauptseite **Master Data Manager** (`http://localhost/MDS`), indem Sie oben auf **SQL Server 2012 Master Data Services** klicken.  
  
2.  Klicken Sie auf **Integrations Management**.  
  
3.  Klicken Sie in der Menüleiste auf **Ansichten erstellen** .  
  
     ![Neue Abonnementsicht hinzufügen (Schaltfläche)](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Neue Abonnementsicht hinzufügen (Schaltfläche)")  
  
4.  Klicken Sie in der Symbolleiste auf das Symbol **+ (Plus Zeichen)** , um eine Abonnement Sicht zu erstellen.  
  
5.  Geben Sie im Bereich **Abonnement Sicht erstellen** den Namen **Suppliers** als **Name der Abonnement Sicht**ein.  
  
6.  Wählen Sie **Suppliers** für **Model**aus.  
  
7.  Wählen Sie **VERSION_1** für die **Version**aus.  
  
8.  Wählen Sie **Lieferant** für **Entität**aus.  
  
9. Wählen Sie **Blatt** Elemente für das **Format**aus.  
  
     ![Abonnementsicht speichern (Schaltfläche)](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Abonnementsicht speichern (Schaltfläche)")  
  
10. Klicken Sie in der Symbolleiste auf **Speichern** , um die Abonnement Ansicht zu speichern. Diese Aktion erstellt eine Ansicht in SQL Server namens **Suppliers**. Sie können dies mit SQL Server Management Studio (SSMS) überprüfen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3 &#40;optionale&#41;: Überprüfen der Abonnement Sichten](task-3-optional-reviewing-the-subscription-views.md)  
  
  
