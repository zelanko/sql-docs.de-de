---
title: Angeben eines alternativen Speicherortes für den Momentaufnahmeordner (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48168354fd6609e4e43571c53c99cb80193aa98e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256112"
---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>Angeben eines alternativen Speicherortes für den Momentaufnahmeordner (SQL Server Management Studio)
  Geben Sie im Dialogfeld **Veröffentlichungseigenschaften -** Veröffentlichung> **auf der Seite \<Momentaufnahme** einen alternativen Momentaufnahmespeicherort an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>So geben Sie einen alternativen Momentaufnahmespeicherort an  
  
1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:  
  
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.  
  
        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../security/secure-the-snapshot-folder.md).  
  
    2.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.  
  
     Zum Komprimieren von Momentaufnahmedateien aktivieren Sie **Momentaufnahmedateien in diesem Ordner komprimieren**. Die Komprimierung wird in der Regel für Verbindungen mit niedriger Bandbreite und für alternative Momentaufnahmespeicherorte auf Wechselmedien verwendet, z. B. einer CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../alternate-snapshot-folder-locations.md)   
 [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Angeben des standardmäßigen Momentaufnahmespeicherorts &#40;SQL Server Management Studio&#41;](../specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../initialize-a-subscription-with-a-snapshot.md)  
  
  
