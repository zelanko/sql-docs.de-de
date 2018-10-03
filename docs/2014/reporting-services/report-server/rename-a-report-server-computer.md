---
title: Umbenennen eines Berichtsservercomputers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c040f3afade749772ae1560e9f99af8cd4ac0a85
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114290"
---
# <a name="rename-a-report-server-computer"></a>Umbenennen eines Berichtsservercomputers
  Durch das Umbenennen eines Computers wird eine entsprechende Namensänderung für den Webserver und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verursacht (falls sie auf demselben Computer installiert ist). In einigen Fällen kann nach einer Computernamensänderung möglicherweise nicht mehr auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zugegriffen werden. Führen Sie die Schritte in diesem Thema aus, um einen Berichtsserver nach einer Änderung des Computernamens neu zu konfigurieren.  
  
## <a name="renaming-a-sql-server-database-engine"></a>Umbenennen einer SQL Server-Datenbank-Engine  
 Wenn Sie Umbenennen der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz, die die Berichtsserver-Datenbank ausgeführt wird. Gehen Sie folgendermaßen vor:  
  
1.  Starten Sie das Reporting Services-Konfigurationstool, und stellen Sie eine Verbindung mit dem Berichtsserver her, der die Berichtsserver-Datenbank auf dem umbenannten Server verwendet.  
  
2.  Öffnen Sie die Seite Setup der Datenbank.  
  
3.  Geben Sie unter **Servername**den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Namen ein, und klicken Sie anschließend auf **Verbinden**.  
  
4.  Klicken Sie auf **Anwenden**.  
  
 Falls der Berichtsserver eine lokale [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz verwendet, können Sie den Server mit *(local)* oder *(local)\instancename* angeben. Wenn Sie mit *(local)* auf den Server verweisen, sind die Verbindungen mit dem Server auch nach einer Umbenennung des Servers weiterhin funktionsfähig. Wenn Sie einen Remoteserver verwenden oder wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mithilfe des Servernamens konfiguriert ist, müssen Sie die Datenbank-Verbindungsinformationen bei jeder Änderung des Servernamens aktualisieren.  
  
## <a name="renaming-a-report-server-computer"></a>Umbenennen eines Berichtsservercomputers  
 Führen Sie die folgenden Aktionen aus, wenn Sie einen Computer umbenannt haben, auf dem ein Berichtsserver ausgeführt wird:  
  
1.  Open **"rsreportserver.config"** in einem Text-Editor, und Ändern der `UrlRoot` Einstellung aus, um den neuen Servernamen wiedergibt. Die `UrlRoot`-Einstellung wird von Übermittlungserweiterungen zum Angeben der URL für den Zugriff auf Elemente verwendet, die auf dem Berichtsserver gespeichert sind. URL-Adresse des Berichtsservers ändern, müssen Sie aktualisieren die `UrlRoot` festlegen, damit weiterhin Abonnements zum Übermitteln von Berichten, wie erwartet.  
  
2.  Wenn sie festgelegt ist, ändern Sie in der gleichen Datei die `ReportServerUrl` Einstellung aus, um den neuen Servernamen wiedergibt. Beachten Sie, dass diese Einstellung nicht in jeder Installation verwendet wird. Falls die Einstellung leer ist, brauchen Sie nichts zu tun.  
  
    > [!NOTE]  
    >  Falls Sie WINS (Windows Internet Naming Service) im Unternehmensnetzwerk verwenden, sind der Berichtsserver und der Berichts-Manager möglicherweise noch eine Zeit lang unter dem vorherigen Namen verfügbar. WINS ordnet jedem Computer, für den es einen Dienst bereitstellt, eine IP-Adresse zu. Nachdem die IP-Adresse für den umbenannten Computer von WINS aktualisiert wurde, kann über den alten Computernamen nicht mehr auf einen Berichtsserver oder auf den Berichts-Manager zugegriffen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [RSReportServer-Konfigurationsdatei](rsreportserver-config-configuration-file.md)   
 [Reporting Services-Konfigurations-Manager &#40;im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](reporting-services-report-server-native-mode.md)   
 [Starten Sie und beenden Sie des Berichtsserverdiensts](start-and-stop-the-report-server-service.md)   
 [rsconfig-Hilfsprogramm (SSRS)](../tools/rsconfig-utility-ssrs.md)  
  
  
