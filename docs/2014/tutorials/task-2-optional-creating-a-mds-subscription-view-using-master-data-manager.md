---
title: 'Aufgabe 2 (Optional): Erstellen einer MDS-Abonnementsicht mithilfe von Master Data Manager | Microsoft Docs'
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
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4883d4f5c7bef05de9625c2fcb7bac235c0306e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161935"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Aufgabe 2 (optional): Erstellen einer MDS-Abonnementsicht mithilfe von Master Data Manager
  In dieser Aufgabe erstellen Sie eine Abonnementsicht verfügbar machen die **Lieferanten** Entität in der **Lieferanten** Modell für andere Anwendungen. Sie verwenden diese Sicht nicht in der aktuellen Version des Lernprogramms.  
  
1.  Wechseln Sie zur Hauptseite des **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)) durch Klicken auf **SQL Server 2012 Master Data Services** oben.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Klicken Sie auf **Erstellen von Sichten** in der Menüleiste.  
  
     ![Eine neues Abonnement Ansichtsschaltfläche "hinzufügen"](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "eine neues Abonnement Ansichtsschaltfläche \"hinzufügen\"")  
  
4.  Klicken Sie auf **+ (Plus)** Symbol auf der Symbolleiste können Sie eine Abonnementsicht erstellt haben.  
  
5.  In der **Abonnementsicht erstellen** Geben Sie im Bereich **Lieferanten** für **Name der Abonnementsicht**.  
  
6.  Wählen Sie **Lieferanten** für **Modell**.  
  
7.  Wählen Sie **VERSION_1** für **Version**.  
  
8.  Wählen Sie **Lieferanten** für **Entität**.  
  
9. Wählen Sie **Blattelemente** für **Format**.  
  
     ![Speichern Sie die Schaltfläche "Ansicht" Abonnements](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "speichern-Schaltfläche \"Abonnement anzeigen\"")  
  
10. Klicken Sie auf **speichern** auf der Symbolleiste, um die Abonnementsicht zu speichern. Diese Aktion erstellt eine Ansicht in SQL Server mit dem Namen **Lieferanten**. Sie können dies mit SQL Server Management Studio (SSMS) überprüfen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3 &#40;Optional&#41;: Überprüfung der Abonnementsichten](task-3-optional-reviewing-the-subscription-views.md)  
  
  