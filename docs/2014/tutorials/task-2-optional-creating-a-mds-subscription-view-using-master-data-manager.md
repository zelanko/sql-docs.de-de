---
title: 'Aufgabe 2 (optional): Erstellen einer MDS-Abonnementansicht mit Demstammdaten-Manager | Microsoft Docs'
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484710"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Aufgabe 2 (optional): Erstellen einer MDS-Abonnementsicht mithilfe des Master Data Manager
  In dieser Aufgabe erstellen Sie eine Abonnementansicht, um die **Supplier-Entität** im **Lieferantenmodell** für andere Anwendungen verfügbar zu machen. Sie verwenden diese Sicht nicht in der aktuellen Version des Lernprogramms.  
  
1.  Wechseln Sie zur Hauptseite des`http://localhost/MDS`Master Data **Managers** ( ), indem Sie oben auf SQL Server **2012 Master Data Services** klicken.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Klicken Sie in der Menüleiste auf **Ansichten erstellen.**  
  
     ![Neue Abonnementsicht hinzufügen (Schaltfläche)](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Neue Abonnementsicht hinzufügen (Schaltfläche)")  
  
4.  Klicken Sie auf der Symbolleiste auf **+ (Plus),** um eine Abonnementansicht zu erstellen.  
  
5.  Geben Sie im Bereich **Abonnementansicht erstellen** den Namen **der Ansicht "Lieferanten** für **Abonnement"** ein.  
  
6.  Wählen Sie **Lieferanten** für **Modell**aus.  
  
7.  Wählen Sie **VERSION_1** für **Version**.  
  
8.  Wählen Sie **Lieferant** für **Entität**aus.  
  
9. Wählen Sie **Blattelemente** für **Format**aus.  
  
     ![Abonnementsicht speichern (Schaltfläche)](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Abonnementsicht speichern (Schaltfläche)")  
  
10. Klicken Sie auf der Symbolleiste auf **Speichern,** um die Abonnementansicht zu speichern. Mit dieser Aktion wird eine Ansicht in SQL Server mit dem Namen **Suppliers**erstellt. Sie können dies mit SQL Server Management Studio (SSMS) überprüfen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3 &#40;Optionaler&#41;: Überprüfen der Abonnementansichten](task-3-optional-reviewing-the-subscription-views.md)  
  
  
