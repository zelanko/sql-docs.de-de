---
title: Komprimieren von Momentaufnahmedateien (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 70b8ec331bcc1d14174a4efb9d9808820ad62c04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162229"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>Komprimieren von Momentaufnahmedateien (SQL Server Management Studio)
  Auf der Seite **Momentaufnahme** können Sie im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** angeben, dass Dateien komprimiert werden sollen. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-compress-snapshot-files"></a>So komprimieren Sie Momentaufnahmedateien  
  
1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:  
  
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.  
  
        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad (Universal Naming Convention) angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Sichern des Momentaufnahmeordners](../security/secure-the-snapshot-folder.md).  
  
    2.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.  
  
        > [!NOTE]  
        >  Wenn dieses Kontrollkästchen aktiviert ist, werden die im Standardordner gespeicherten Dateien nicht komprimiert. Komprimierte Dateien können nur im alternativen im vorigen Schritt angegebenen Speicherort gespeichert werden.  
  
2.  Wählen Sie **Momentaufnahmedateien in diesem Ordner komprimieren**aus.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Komprimierte Momentaufnahmen](../compressed-snapshots.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../initialize-a-subscription-with-a-snapshot.md)  
  
  