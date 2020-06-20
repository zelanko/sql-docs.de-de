---
title: Paketverwaltung (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, managing
- packages [Integration Services], managing
- Integration Services packages, managing
- storing packages
- Stored Packages folder
- current packages
- Running Packages folder
- status information [Integration Services]
- SSIS packages, managing
- storage [Integration Services]
- monitoring [Integration Services], packages
- Integration Services service, package management
- services [Integration Services], package management
ms.assetid: 0261ed9e-3b01-4e37-a9d4-d039c41029b6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1ca2e8dd516b995dcf3d2e48b1ed14209677d41f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963481"
---
# <a name="package-management-ssis-service"></a>Paketverwaltung (SSIS-Dienst)
  Die Verwaltung von Paketen beinhaltet u. a. die folgenden Tasks:  
  
-   Überwachen von ausgeführten Paketen  
  
-   Verwalten des Paketspeichers  
  
-   Importieren und Exportieren von Paketen  
  
> [!IMPORTANT]  
>  In diesem Thema wird der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
## <a name="package-store"></a>Paketspeicher  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]stellt zwei Ordner der obersten Ebene für den Zugriff auf [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete bereit: **Ausführen von Paketen** und **gespeicherten Paketen**. Der Ordner **Ausgeführte Pakete** enthält eine Auflistung der Pakete, die derzeit auf dem Server ausgeführt werden. Im Ordner **Gespeicherte Pakete** sind die im Paketspeicher gespeicherten Pakete aufgelistet. Hierbei handelt es sich um die einzigen vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst verwalteten Pakete. Der Paketspeicher kann aus den msdb-Datenbank- und/oder den Dateisystemordnern bestehen, die in der Konfigurationsdatei des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Diensts aufgelistet sind. In der Konfigurationsdatei sind die zu verwaltenden msdb- und Dateisystemordner angegeben. Sie können Pakete auch an anderen Stellen des Dateisystems speichern, die nicht vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst verwaltet werden.  
  
 Pakete, die Sie in der msdb-Datenbank speichern, werden in einer Tabelle mit dem Namen „sysssispackages“ gespeichert. Beim Speichern von Paketen in der msdb-Datenbank können Sie die Pakete in logischen Ordnern gruppieren. Die Verwendung von logischen Ordnern ermöglicht Ihnen, die Pakete nach dem Einsatzzweck zu sortieren oder sie in der „sysssispackages“-Tabelle zu filtern. Neue logische Ordner können Sie mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen. Standardmäßig werden alle logischen Ordner, die Sie der msdb-Datenbank hinzufügen, automatisch in den Paketspeicher übernommen.  
  
 Die logischen Ordner, die Sie zum Gruppieren von Paketen in der msdb-Datenbank erstellen, werden in der „sysssispackagefolders“-Tabelle der msdb-Datenbank als Zeilen dargestellt. Die Spalten „folderid“ und „parentfolderid“ in der „sysssispackagefolders“-Tabelle definieren die Ordnerhierarchie. Die logischen Stammordner in der msdb-Datenbank sind die Zeilen in der „sysssispackagefolders“-Tabelle, die in der „parentfolderid“-Spalte NULL-Werte aufweisen. Weitere Informationen finden Sie unter [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql) und [sysssispackagefolders &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackagefolders-transact-sql).  
  
 Wenn Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen und eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen, werden die msdb-Ordner, die vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst verwaltet werden, im Ordner „Gespeicherte Pakete“ aufgelistet. Wenn in der Konfigurationsdatei Stammdateisystemordner angegeben sind, werden im Ordner Gespeicherte Pakete auch die Pakete aufgelistet, die in diesen Ordnern sowie deren Unterordnern gespeichert sind.  
  
 Sie können Pakete in beliebigen Dateisystemordnern speichern. Diese werden jedoch nur dann in den Unterordnern des Ordners **Gespeicherte Pakete** aufgeführt, wenn die betreffenden Dateisystemordner der Liste der Ordner in der Konfigurationsdatei für den Paketspeicher hinzugefügt wurden. Weitere Informationen zur Konfigurationsdatei finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](integration-services-service-ssis-service.md).  
  
 Der Ordner **Ausgeführte Pakete** enthält keine Unterordner und ist nicht erweiterbar.  
  
 Der Ordner **Gespeicherte Pakete** enthält standardmäßig zwei Ordner: **Dateisystem** und **MSDB**. Im Ordner **Dateisystem** sind die im Dateisystem gespeicherten Pakete aufgelistet. Der Speicherort dieser Dateien wird in der Konfigurationsdatei für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst angegeben. Der Standardordner ist der Paketordner, der sich in %Programme%\Microsoft SQL Server\100\DTS befindet. Der Ordner **MSDB** enthält eine Liste der in der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -msdb-Datenbank auf dem Server gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Pakete. Die „sysssispackages“-Tabelle enthält die in msdb gespeicherten Pakete.  
  
 Zum Anzeigen der Liste der Pakete im Paketspeicher müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen und eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen. Weitere Informationen finden Sie unter [Anzeigen von Integration Services-Paketen in SQL Server Management Studio &#40;SSIS-Dienst&#41;](../view-integration-services-packages-in-sql-server-management-studio-ssis-service.md).  
  
## <a name="monitoring-running-packages"></a>Überwachen von ausgeführten Paketen  
 Der Ordner **Ausgeführte Pakete** enthält eine Liste der Pakete, die derzeit ausgeführt werden. Wenn Sie Informationen zu den aktuellen Paketen auf der Seite **Zusammenfassung** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen möchten, klicken Sie auf den Ordner **Ausgeführte Pakete** . Informationen wie die Ausführungsdauer der ausgeführten Pakete werden auf der Seite **Zusammenfassung** angezeigt. Sie können den Ordner aktualisieren, um die aktuellsten Informationen anzuzeigen.  
  
 Wenn Sie Informationen zu einem einzelnen ausgeführten Paket auf der Seite **Zusammenfassung** anzeigen möchten, klicken Sie auf das Paket. Auf der Seite **Zusammenfassung** werden Informationen wie die Version und die Beschreibung des Pakets angezeigt.  
  
 Sie können ein ausgeführtes Paket im Ordner **Ausgeführte Pakete** beenden, indem Sie mit der rechten Maustaste auf das Paket und anschließend auf **Beenden**klicken.  
  
## <a name="managing-package-storage"></a>Verwalten des Paketspeichers  
 Für die Organisation von Paketen können Sie den Paketspeicher-Stammordnern benutzerdefinierte Ordner hinzufügen, die vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst in der Konfigurationsdatei aufgelistet werden. Standardmäßig lauten die Stammordner **Dateisystem** und **MSDB** . So können Sie beispielsweise dem Ordner **Dateisystem** einen Ordner **Datenbereinigung** hinzufügen, der alle Pakete enthält, die zum Bereinigen von Daten verwendet werden. Sie können benutzerdefinierten Ordnern benutzerdefinierte Ordner hinzufügen und so eine verschachtelte Ordnerhierarchie für Ihre speziellen Anforderungen erstellen. Die benutzerdefinierten Ordner können gelöscht und umbenannt werden. Die in der Konfigurationsdatei angegebenen Stammordner können jedoch nicht umbenannt oder gelöscht werden. Um die Stammordner zu aktualisieren, die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aufgelistet werden, müssen Sie die Konfigurationsdatei aktualisieren.  
  
 Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](../configuring-the-integration-services-service-ssis-service.md).  
  
## <a name="importing-and-exporting-packages"></a>Importieren und Exportieren von Paketen  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete können entweder in der msdb-Datenbank oder im Dateisystem gespeichert werden. Sie können ein Paket mit der Import- oder Exportfunktion von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] von einem Speichertyp in einen anderen kopieren. Sie können ein Paket auch in denselben Speichertyp importieren und das Paket umbenennen, um eine Kopie eines Pakets erstellen zu können. Das **dtutil** -Eingabeaufforderungs-Hilfsprogramm (dtutil.exe) kann auch zum Importieren und Exportieren von Paketen verwendet werden.  
  
 Weitere Informationen finden Sie unter [dtutil Utility](../dtutil-utility.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Importieren und Exportieren von Paketen &#40;SSIS-Dienst&#41;](../import-and-export-packages-ssis-service.md)  
  
-   [Anzeigen von Integration Services-Paketen in SQL Server Management Studio &#40;SSIS-Dienst&#41;](../view-integration-services-packages-in-sql-server-management-studio-ssis-service.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Dienst &#40;SSIS-Dienst&#41;](integration-services-service-ssis-service.md)  
  
  
