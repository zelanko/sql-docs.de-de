---
title: Umbenennen eines Berichtsservercomputers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23c96ae889017eab71378b91eeb1a9ea1881fb25
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103499"
---
# <a name="rename-a-report-server-computer"></a>Umbenennen eines Berichtsservercomputers
  Durch das Umbenennen eines Computers wird eine entsprechende Namensänderung für den Webserver und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verursacht (falls sie auf demselben Computer installiert ist). In einigen Fällen kann nach einer Computernamensänderung möglicherweise nicht mehr auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zugegriffen werden. Führen Sie die Schritte in diesem Thema aus, um einen Berichtsserver nach einer Änderung des Computernamens neu zu konfigurieren.  
  
## <a name="renaming-a-sql-server-database-engine"></a>Umbenennen einer SQL Server-Datenbank-Engine  
 Führen Sie die folgenden Aktionen aus, wenn Sie die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz umbenannt haben, in der die Berichtsserver-Datenbank ausgeführt wird:  
  
1.  Starten Sie das Reporting Services-Konfigurationstool, und stellen Sie eine Verbindung mit dem Berichtsserver her, der die Berichtsserver-Datenbank auf dem umbenannten Server verwendet.  
  
2.  Öffnen Sie die Seite Setup der Datenbank.  
  
3.  Geben Sie unter **Servername**den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Namen ein, und klicken Sie anschließend auf **Verbinden**.  
  
4.  Klicken Sie auf **Anwenden**.  
  
 Falls der Berichtsserver eine lokale [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz verwendet, können Sie den Server mit *(local)* oder *(local)\instancename* angeben. Wenn Sie mit *(local)* auf den Server verweisen, sind die Verbindungen mit dem Server auch nach einer Umbenennung des Servers weiterhin funktionsfähig. Wenn Sie einen Remoteserver verwenden oder wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mithilfe des Servernamens konfiguriert ist, müssen Sie die Datenbank-Verbindungsinformationen bei jeder Änderung des Servernamens aktualisieren.  
  
## <a name="renaming-a-report-server-computer"></a>Umbenennen eines Berichtsservercomputers  
 Führen Sie die folgenden Aktionen aus, wenn Sie einen Computer umbenannt haben, auf dem ein Berichtsserver ausgeführt wird:  
  
1.  Öffnen Sie **RSReportServer. config** in einem Text-Editor, `UrlRoot` und ändern Sie die Einstellung, um den neuen Servernamen widerzuspiegeln. Die `UrlRoot`-Einstellung wird von Übermittlungserweiterungen zum Angeben der URL für den Zugriff auf Elemente verwendet, die auf dem Berichtsserver gespeichert sind. Wenn Sie die URL-Adresse des Berichtsservers ändern, müssen Sie die `UrlRoot`-Einstellung aktualisieren, damit Berichte weiterhin erwartungsgemäß von Abonnements übermittelt werden.  
  
2.  Ändern Sie in der gleichen Datei ggf. die `ReportServerUrl`-Einstellung so, dass sie den neuen Servernamen wiedergibt. Beachten Sie, dass diese Einstellung nicht in jeder Installation verwendet wird. Falls die Einstellung leer ist, brauchen Sie nichts zu tun.  
  
    > [!NOTE]  
    >  Falls Sie WINS (Windows Internet Naming Service) im Unternehmensnetzwerk verwenden, sind der Berichtsserver und der Berichts-Manager möglicherweise noch eine Zeit lang unter dem vorherigen Namen verfügbar. WINS ordnet jedem Computer, für den es einen Dienst bereitstellt, eine IP-Adresse zu. Nachdem die IP-Adresse für den umbenannten Computer von WINS aktualisiert wurde, kann über den alten Computernamen nicht mehr auf einen Berichtsserver oder auf den Berichts-Manager zugegriffen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RSReportServer-Konfigurationsdatei](rsreportserver-config-configuration-file.md)   
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](reporting-services-report-server-native-mode.md)   
 [Starten und Beenden des Berichtsserverdiensts](start-and-stop-the-report-server-service.md)   
 [rsconfig-Hilfsprogramm (SSRS)](../tools/rsconfig-utility-ssrs.md)  
  
  
