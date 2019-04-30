---
title: Starten und Beenden des Berichtsserverdiensts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4bd22faaa9d0f3b6ce213c37e20615492b1e95d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190817"
---
# <a name="start-and-stop-the-report-server-service"></a>Starten und Beenden des Berichtsserverdiensts
  Der Berichtsserver wird als Windows-Dienst implementiert, der den Report Server-Webdienst, den Berichts-Manager und eine Hintergrundverarbeitungsanwendung umfasst. Der Dienst muss ausgeführt werden, damit Sie die Berichtsserverfunktionalitäten nutzen können. Durch Beenden des Diensts werden alle Berichtsservervorgänge beendet.  
  
 Wenn der Dienst beendet ist, werden Anforderungen für die Verarbeitung von geplanten Berichts- und Abonnementverarbeitungen in die Warteschlange gestellt. Dies liegt daran, dass diese Ereignisse von vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführten Aufträgen erstellt werden. Wenn Sie einen Backlog von Vorgängen vermeiden möchten, während der Dienst deaktiviert ist, sollten Sie erwägen, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ebenfalls zu beenden.  
  
 Sie können den Berichtsserverdienst mit einer Vielzahl von Tools starten oder beenden, u.&nbsp;a. mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager und dem Services-Tool von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Wenn Sie über das Starten und Beenden des Diensts hinaus weitere Vorgänge durchführen möchten, z.&nbsp;B. Ändern des Dienstkontos, müssen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool verwenden. Wenn Sie zum Ändern des Dienstkontos andere Tools verwenden, kann dadurch Ihre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation beschädigt werden. Weitere Informationen finden Sie unter [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
 Der Dienst kann nicht angehalten und fortgesetzt werden. Es gibt keine Startparameter. Obwohl keine expliziten Abhängigkeiten vorhanden sind, muss der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt werden, wenn auf dem Berichtsserver Abonnements oder geplante Berichtsvorgänge unterstützt werden sollen.  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a>So starten oder beenden Sie den Dienst mit dem Reporting Services-Konfigurationstool  
  
1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und stellen Sie eine Verbindung mit dem Berichtsserver her.  
  
2.  Klicken Sie auf der Seite Berichtsserverstatus auf **Beenden** oder auf **Starten**.  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a>So starten oder beenden Sie den Dienst mit der Option Dienste unter Verwaltung  
  
-   Öffnen Sie unter „Verwaltung“ den Eintrag „Dienste“, klicken Sie mit der rechten Maustaste auf **SQL Server Reporting Services (MSSQLSERVER)**, und klicken Sie auf **Beenden** bzw. **Neu starten**.  
  
 Wenn mehrere Instanzen ausgeführt werden oder der Berichtsserver als eine benannte Instanz ausgeführt wird, überprüfen Sie, ob der Instanzname in Klammern der Berichtsserverinstanz entspricht, die beendet oder neu gestartet werden soll.  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a>So starten oder beenden Sie den Dienst mit dem SQL Server-Konfigurations-Manager  
  
1.  Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
2.  Wählen Sie „SQL Server-Dienste“ aus, klicken Sie mit der rechten Maustaste auf **SQL Server Reporting Services**, und klicken Sie auf **Beenden** oder **Neu starten**.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
