---
title: Reporting Services-Konfigurationsoptionen (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.reportserverinstoptions.f1
helpviewer_keywords:
- Report Server Installation Options page [SQL Server Installation Wizard]
- report servers [Reporting Services], installing
- SQL Server Installation Wizard, Report Server Installation Options page
ms.assetid: e4561f6c-bc7f-467e-821a-cde8e5cd7391
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 67c1cf99f536b7cc6de0cef3633af19ae88014a5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092590"
---
# <a name="reporting-services-configuration-options-ssrs"></a>Reporting Services-Konfigurationsoptionen (SSRS)
  Auf der Seite **Reporting Services-Konfiguration** des Installations-Assistenten für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie die Optionen für das Installieren und Konfigurieren eines Berichtsservers angeben. Die Verfügbarkeit einer Installationsoption ist von den Optionen abhängig, die Sie auf der Seite **Funktionsauswahl** ausgewählt haben, und richtet sich danach, ob Sie gleichzeitig mit dem Berichtsserver auch eine lokale Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installieren.  
  
 Wenn ein SSL-Zertifikat (Secure Sockets Layer) auf dem Computer installiert und an ein starkes Platzhalterzeichen gebunden ist, werden Reporting Services-URLs von Setup in einigen Fällen mit HTTPS-Präfix erstellt. Weitere Informationen über die Zuordnung von Zertifikaten zu Reporting Services-URLs finden Sie unter [Konfigurieren eines Berichtsservers für Secure Sockets Layer (SSL) Connections](https://go.microsoft.com/fwlink/?LinkId=199089) (https://go.microsoft.com/fwlink/?LinkId=199089) in SQL Server-Onlinedokumentation.  
  
 Die neuesten Informationen zur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und die Installation und Konfiguration dieser Version finden Sie unter [zusätzliche Installationsinformationen](https://go.microsoft.com/fwlink/?LinkId=207425) (https://go.microsoft.com/fwlink/?LinkId=207425).  
  
## <a name="options"></a>Optionen  
  
### <a name="reporting-services-native-mode"></a>Einheitlicher Modus von Reporting Services  
 Wenn Setup keine Standardkonfiguration des Berichtsservers ausführen kann, weil mindestens eine Anforderung nicht erfüllt wird, lässt der Installations-Assistent nur die Option für die minimale Installation zu. Dabei werden die erforderlichen Dateien kopiert, nach Abschluss der Installation muss jedoch ein Berichtsserver im einheitlichen Modus mithilfe des Konfigurations-Managers für Reporting Services konfiguriert werden.  
  
> [!NOTE]  
>  Eine vorhandene Berichtsserver-Datenbankdatei verursacht möglicherweise einen Fehler beim Setup, wenn Sie eine der Standardinstallationsoptionen auswählen. Wenn Sie eine Standardinstallationsoption auswählen, versucht Setup, eine Berichtsserver-Datenbank mit dem Standardnamen zu erstellen. Wenn bereits eine Datenbank mit diesem Namen vorhanden ist, tritt ein Fehler beim Setup auf, und Sie müssen ein Rollback für die Installation ausführen. Um dieses Problem zu vermeiden, können Sie die vorhandene Datenbank umbenennen, bevor Sie Setup ausführen, oder die Option **Nur installieren** auswählen, sodass Sie benutzerdefinierte Datenbankeinstellungen angeben können, wenn Setup beendet ist.  
  
#### <a name="install-and-configure"></a>Installieren und konfigurieren  
 Installiert eine Berichtsserverinstanz im einheitlichen Modus mit den Standardwerten für die Berichtsserver-Datenbanken und das Dienstkonto sowie die URL-Reservierungen. Wenn Sie diese Option auswählen, kann die Berichtsserverinstanz verwendet werden, wenn das Setup fertig gestellt ist. Das Setup erstellt die Berichtsserver-Datenbank mithilfe einer lokalen Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und konfiguriert einen Berichtsserver so, dass Standardwerte verwendet werden.  
  
 Diese Option steht nur zur Verfügung, wenn die Standardwerte, die in einer Berichtsserverinstallation verwendet werden, für Ihr System gültig sind. Diese Option wird für Entwickler empfohlen, die alle Komponenten lokal installieren möchten, sowie für Benutzer, die die Software evaluieren.  
  
 Klicken Sie auf **Details**, um Informationen über die Standardeinstellungen anzuzeigen, die das Setup verwendet, oder um festzustellen, warum die Standardkonfiguration nicht installiert werden kann. Weitere Informationen über die Standardkonfiguration für einen Berichtsserver im einheitlichen Modus finden Sie unter [Standardkonfiguration für die Installation im einheitlichen Modus (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199091) (https://go.microsoft.com/fwlink/?LinkId=199091).  
  
#### <a name="install-only"></a>Nur installieren  
 Installiert die Berichtsserver-Programmdateien, erstellt das Berichtsserver-Dienstkonto und registriert den Windows-Verwaltungsinstrumentationsanbieter des Berichtsservers. Diese Installationsoption wird als "Nur Dateien"-Installation bezeichnet. Wählen Sie diese Option aus, wenn Sie die Standardkonfiguration nicht verwenden möchten. Wenn die Standardkonfiguration nicht installiert werden kann oder wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster installieren, das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]enthält, ist dies die einzige verfügbare Option. Weitere Informationen zu einer ausschließlichen Datei-Installation, finden Sie unter [ausschließliche Datei-Installation (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199093) (https://go.microsoft.com/fwlink/?LinkId=199093).  
  
 Nach Abschluss des Setups müssen Sie die Berichtsserver-Datenbank erstellen und den Berichtsserver konfigurieren, bevor Sie ihn verwenden können. Verwenden Sie zum Konfigurieren eines Berichtsservers und Erstellen der Datenbank den Reporting Services-Konfigurations-Manager. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eine Berichtsserver-Datenbank (Reporting Services-Konfiguration)](https://go.microsoft.com/fwlink/?LinkId=199094) (https://go.microsoft.com/fwlink/?LinkId=199094) und [Konfigurieren einer Berichtsserver-Datenbankverbindung](https://go.microsoft.com/fwlink/?LinkId=199095) (https://go.microsoft.com/fwlink/?LinkId=199095).  
  
### <a name="reporting-services-sharepoint-mode"></a>SharePoint-Modus von Reporting Services  
  
#### <a name="install-only"></a>Nur installieren  
 Installiert die Berichtsserver-Programmdateien und PowerShell-Cmdlets. Wenn die Installation abgeschlossen ist, müssen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services starten und eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung erstellen. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [Installieren von Reporting Services-Berichtsserver im SharePoint-Modus für Power View und Datenwarnungen](https://go.microsoft.com/fwlink/?LinkId=207543) (https://go.microsoft.com/fwlink/?LinkId=207543).  
  
-   [Installieren von Reporting Services im SharePoint-Modus als einzelne Serverfarm](https://go.microsoft.com/fwlink/?LinkId=207544) (https://go.microsoft.com/fwlink/?LinkId=207544).  
  
-   [Reporting Services Report Server (SSRS)](https://go.microsoft.com/fwlink/?LinkID=207244) (https://go.microsoft.com/fwlink/?LinkID=207244).  
  
## <a name="installing-the-reporting-services-add-in-for-sharepoint-technologies"></a>Installieren des Reporting Services-Add-Ins für SharePoint-Technologien  
 Das Add-In kann ab Version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] als Teil der SQL Server-Installation auf der Seite für die Funktionsauswahl des Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden.  
  
 Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010 kann jedoch mithilfe einer der folgenden Methoden installiert werden:  
  
-   Führen Sie das Vorbereitungstool für SharePoint 2010-Produkte, **PreRequisiteInstaller.exe**, aus.  
  
-   Führen Sie die Installation über das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedium durch. Klicken Sie im Setupordner auf den **-Installationsmedien auf die Datei** rsSharePoint.msi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , nachdem das Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abgeschlossen ist.  
  
-   Laden Sie das Add-In herunter, und installieren Sie es. Weitere Informationen finden Sie unter [, wo Sie das Reporting Services-add-in für SharePoint-Produkte finden](https://go.microsoft.com/fwlink/?LinkID=208634) (https://go.microsoft.com/fwlink/?LinkID=208634).  
  
## <a name="see-also"></a>Siehe auch  
 [Starten Sie den Reporting Services-Konfigurations-Manager](https://go.microsoft.com/fwlink/?LinkId=199096)   
 [Erstellen einer Berichtsserver-Datenbank (Reporting Services-Konfiguration)](https://go.microsoft.com/fwlink/?LinkId=199094)   
 [Aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)   
 [Installieren des SharePoint-Modus und einheitlichen Modus von Reporting Services über die Eingabeaufforderung](https://go.microsoft.com/fwlink/?LinkId=217620)  
  
  
