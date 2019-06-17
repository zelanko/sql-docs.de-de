---
title: Umkehren einer Transaktion (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d44c240962e27f04e44414866c12dcee07b6b50c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65485946"
---
# <a name="reverse-a-transaction-master-data-services"></a>Umkehren einer Transaktion (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine Transaktion umkehren, wenn eine Aktion rückgängig gemacht werden muss. Beispiele für Transaktionen sind Attributwertänderungen, Hierarchieverschiebungen oder Elementlöschungen. Dieses Thema gilt für Transaktionen von Entitäten mit dem Transaktionsprotokolltyp „Attribut“. Wechseln Sie auf die Explorer-Seite der Entität, um den Transaktionsverlauf der Entitäten anzuzeigen, die den Transaktionsprotokolltyp „Element“ aufweisen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Versionsverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-reverse-a-transaction"></a>So kehren Sie eine Transaktion um  
  
1.  Klicken Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite auf **Versionsverwaltung**.  
  
2.  Klicken Sie in der Menüleiste auf **Transaktionen**.  
  
3.  Wählen Sie auf der Seite **Transaktionen** in der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
5.  Klicken Sie auf die Zeile im Raster für die Transaktion, die Sie umkehren möchten.  
  
6.  Klicken Sie auf **Transaktion umkehren**.  
  
7.  Klicken Sie im Bestätigungsdialogfeld auf **OK**. Dem Raster wird eine weitere Transaktion hinzugefügt, um die umgekehrte Transaktion aufzuzeichnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionen &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)   
 [Reaktivieren eines Elements oder einer Sammlung &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
 [Zurücksetzen des Elementrevisionsverlaufs](../master-data-services/rollback-member-revision-history-master-data-services.md)
  
  
