---
title: Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9a598030000e5764cecc8ababa75ef2bdd8598ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056377"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a>Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio
  Nachdem Sie das Projekt auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitgestellt haben, können Sie das Paket auf dem Server ausführen.  
  
 Sie können Vorgangsberichte verwenden, um Informationen über Pakete anzuzeigen, deren Ausführung abgeschlossen ist bzw. die derzeit auf dem Server ausgeführt werden. Weitere Informationen finden Sie unter [Berichte für den Integration Services-Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a>So führen Sie mit SQL Server Management Studio ein Paket auf dem Server aus  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] her, die den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog enthält.  
  
2.  Erweitern Sie im Objekt-Explorer den Knoten **Integration Services-Kataloge** und den Knoten **SSISDB** , und navigieren Sie zu dem Paket, das im bereitgestellten Projekt enthalten ist.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Paketnamen, und wählen Sie **Ausführen**aus.  
  
4.  Konfigurieren Sie die Paketausführung mit den Einstellungen im Dialogfeld **Paket ausführen**auf den Registerkarten **Parameter**, **Verbindungs-Managern** und **Erweitert** .  
  
5.  Klicken Sie auf **OK** , um das Paket auszuführen.  
  
     -oder-  
  
     Verwenden Sie gespeicherte Prozeduren zum Ausführen des Pakets. Klicken Sie auf **Skript** , um die Transact-SQL-Anweisung zu generieren, die eine Instanz der Ausführung erstellt und startet. Die Anweisung enthält einen Aufruf der gespeicherten Prozeduren catalog.create_execution, catalog.set_execution_parameter_value und catalog.start_execution. Weitere Informationen zu diesen gespeicherten Prozeduren finden Sie unter [catalog.create_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) und [catalog.start_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
  
