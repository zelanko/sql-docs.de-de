---
title: Verschieben eines UCPs von einer SQL Server-Instanz in eine andere (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 668fc8f9478c66ea7564d99c455ac43dc905de4b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85023425"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a>Verschieben eines UCPs von einer SQL Server-Instanz in eine andere (SQL Server-Hilfsprogramm)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] einen Steuerungspunkt für das Hilfsprogramm (UCP) von einer Instanz von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in eine andere verschieben.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a>Verschieben Sie einen UCP von einer SQL Server-Instanz in eine andere.  
  
1.  Erstellen Sie einen neuen UCP für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die neue Hostinstanz des UCPs darstellt. Weitere Informationen finden Sie unter [Erstellen eines Steuerungspunkts für das SQL Server-Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).  
  
2.  Wenn nicht standardmäßige Richtlinieneinstellungen für beliebige Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm festgelegt wurden, notieren Sie sich die Richtlinienschwellenwerte, damit Sie sie auf dem neuen UCP entsprechend festlegen können. Standardrichtlinien werden angewendet, sobald dem neuen UCP Instanzen hinzugefügt werden. Wenn Standardrichtlinien gültig sind, wird in der Listenansicht des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms in der Spalte **Richtlinientyp** der Wert **Global** angezeigt.  
  
3.  Entfernen Sie alle verwalteten Instanzen aus dem alten UCP. Weitere Informationen finden Sie unter [Vorgehensweise: Entfernen einer Instanz von SQL Server aus dem SQL Server-Hilfsprogramm](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
4.  Sichern Sie das Utility Management Data Warehouse (UMDW) vom alten UCP aus. Der Dateiname ist Sysutility_mdw_ \<GUID> _data, und der Standard Speicherort der Datenbank lautet \<System drive> : \Programme\Microsoft SQL Server \ MSSQL10_50. <UCP_Name> \MSSQL\Data \\ , wobei \<System drive> normalerweise C:\ ist. Antrie. Weitere Informationen finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md).  
  
5.  Stellen Sie die Sicherung des UMDWs auf dem neuen UCP wieder her. Weitere Informationen finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md).  
  
6.  Registrieren Sie Instanzen im neuen UCP, um sie als verwaltete Instanzen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms einzurichten. Weitere Informationen finden Sie unter [ Registrieren einer Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).  
  
7.  Implementieren Sie ggf. benutzerdefinierte Richtliniendefinitionen für die verwalteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
8.  Warten Sie ungefähr eine Stunde, bis Datensammlungs- und Aggregationsvorgänge abgeschlossen sind.  
  
9. Um Daten zu aktualisieren, klicken Sie mit der rechten Maustaste auf den Knoten **Verwaltete Instanzen** im **Hilfsprogramm-Explorer**, und wählen Sie dann **Aktualisieren**aus. Listenansichtsdaten werden im Inhaltsbereich von **Hilfsprogramm-Explorer** angezeigt. Weitere Informationen finden Sie unter [Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](view-resource-health-policy-results-sql-server-utility.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](sql-server-utility-features-and-tasks.md)   
 [Registrieren einer Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
