---
title: Anwenden und Aktualisieren eines Changesets (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3a6a3cf2-1e77-43d3-a64a-855ae51258e7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 710fb8783b0313a6dd46273ce1821e425f7814d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65483983"
---
# <a name="apply-and-update-a-changeset-master-data-services"></a>Anwenden und Aktualisieren eines Changeset (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Ein Changeset ist eine Auflistung der ausstehenden Änderungen an den Masterdaten. Sie können ein Changeset lokal anwenden, um die ausstehenden Änderungen anzuzeigen, hinzuzufügen, zu aktualisieren bzw. zu löschen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen. Weitere Informationen finden Sie unter [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Sie benötigen mindestens die Berechtigung zum Aktualisieren der Entität oder einer ihrer Attribute.  
  
-   Als Administrator einer Entität können Sie nur das Changeset anzeigen, dessen Eigentümer Sie sind, bzw. das zur Genehmigung vorgelegte Changeset.  
  
-   Sie können nur Ihr eigenes Changeset ändern, und das auch nur, wenn der Status des Changeset "Offen" oder "Abgelehnt" lautet.  
  
## <a name="to-apply-and-update-a-changeset"></a>So wenden Sie ein Changeset an und aktualisieren es  
  
1.  Wählen Sie auf der Startseite von [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ein Modell und eine Version aus, und klicken Sie anschließend auf **Explorer**.  
  
2.  Klicken Sie im Menü **Entitäten** auf eine Entität.  
  
3.  Wählen Sie im rechten Bereich **Changesets** aus, und doppelklicken Sie auf das Changeset, das Sie anzeigen und ändern möchten.  
  
4.  Klicken Sie auf **Anwenden**.  
  
     Die ausstehenden Änderungen werden auf das Entitätselement im Raster angewendet. Die ausstehenden Änderungen werden hervorgehoben.  
  
     Durch Erstellen, Löschen und Aktualisieren von Elementen werden die Änderungen des Changeset angewendet.  
  
5.  Um ausstehende Änderungen wieder zurückzusetzen, klicken Sie im Bereich **Changesets** mit der rechten Maustaste in das Raster, und klicken Sie anschließend auf **Wiederherstellen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Ein Changeset bestätigen oder übermitteln &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Changesets &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Genehmigen oder Ablehnen eines Changesets &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
