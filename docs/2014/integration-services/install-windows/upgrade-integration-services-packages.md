---
title: Durchführen eines Upgrades für Integration Services-Pakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a1ff35cfc7d5e8611c06981b2e3a9fe9dd6e82fd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768996"
---
# <a name="upgrade-integration-services-packages"></a>Aktualisieren von Integration Services-Paketen
  Wenn Sie ein upgrade eine Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] auf die aktuelle Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Ihre vorhandenen [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] Pakete werden nicht automatisch auf das Paketformat, das von der aktuellen Version aktualisiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] wird verwendet. Sie müssen eine Upgrademethode auswählen und die Pakete manuell aktualisieren.  
  
 Wenn Sie ein [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paket aktualisieren, migriert [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] die Skripts in allen Skripttasks und Skriptkomponenten zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wurde für die Skripts in Skripttasks und Skriptkomponenten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] für Applikationen (VSA) verwendet. Weitere Informationen zu Änderungen, die möglicherweise vor der Migration an Skripts vorgenommen werden müssen und zu Fehlern bei der Skriptkonvertierung führen, finden Sie unter [Migrieren von Skripts zu VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).  
  
 Für Informationen zum Aktualisieren von Paketen beim Konvertieren eines Projekts für das Projektbereitstellungsmodell finden Sie unter [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).  
  
## <a name="sql-server-2000-data-transformation-services-packages"></a>SQL Server 2000 Data Transformation Services-Pakete  
 Unterstützung für das Migrieren oder Ausführen von Paketen für Data Transformation Services (DTS) in der aktuellen Version von nicht mehr [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Folgende DTS-Funktionen werden nicht mehr unterstützt:  
  
-   DTS-Laufzeit  
  
-   DTS-API  
  
-   Paketmigrations-Assistent zum Migrieren von DTS-Paketen zur nächsten Version von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Unterstützung der DTS-Paketverwaltung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   DTS 2000-Paket ausführen (Task)  
  
-   Scannen von DTS-Paketen durch den Upgrade Advisor  
  
 Die nachstehenden Optionen sind für das Migrieren von DTS-Paketen verfügbar.  
  
-   Migrieren Sie die Pakete zu [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], und aktualisieren Sie dann die Pakete auf [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Informationen zum Migrieren von DTS-Paketen zu [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] und [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] finden Sie unter [Migrieren von Data Transformation Services-Paketen](https://go.microsoft.com/fwlink/?LinkId=251870) (2005) und [Migrieren von Data Transformation Services-Paketen](https://go.microsoft.com/fwlink/?LinkId=251871) (2008).  
  
-   Erstellen Sie die DTS-Pakete mithilfe von [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] erneut.  
  
     Informationen zu den neuen Funktionen in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] finden Sie unter [Neuigkeiten &#40;Integration Services&#41;](../what-s-new-in-integration-services-in-sql-server-2016.md). Eine Übersicht über die Struktur von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Paketen finden Sie unter [Integration Services-Pakete & #40; SSIS- & #41;](../integration-services-ssis-packages.md).  
  
## <a name="selecting-an-upgrade-method"></a>Auswählen einer Upgrademethode  
 Sie können verschiedene Methoden verwenden, um [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Pakete zu aktualisieren. Bei einigen dieser Methoden wird das Upgrade nur temporär ausgeführt. Bei anderen wird das Upgrade dauerhaft ausgeführt. In der folgenden Tabelle wird jede dieser Methoden beschrieben, und es wird angegeben, ob das Upgrade temporär oder dauerhaft ausgeführt wird.  
  
> [!NOTE]  
>  Wenn Sie ein [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Paket mithilfe des Hilfsprogramms **dtexec** (dtexec.exe) ausführen, das mit der aktuellen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wird, verlängert sich die Ausführungszeit für das Upgrade des temporären Pakets. Dabei hängt es von der Paketgröße ab, um welchen Zeitraum sich die Ausführungszeit verlängert. Zur Vermeidung einer längeren Ausführungszeit wird empfohlen, das Paket vor der Ausführung zu aktualisieren.  
  
|Upgrademethode|Typ des Upgrades|  
|--------------------|---------------------|  
|Verwenden Sie das Hilfsprogramm **dtexec** (dtexec.exe), das mit der aktuellen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wird, um ein [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Paket auszuführen.<br /><br /> Weitere Informationen finden Sie unter [dtexec Utility](../packages/dtexec-utility.md).|Das Paketupgrade ist vorübergehend. Bei einem [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paket ist die Skriptmigration temporär.<br /><br /> Der Änderungen können nicht gespeichert werden.|  
|Öffnen Sie eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- oder eine [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Paketdatei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|Das Paketupgrade wird dauerhaft ausgeführt, wenn Sie das Paket speichern. Wenn Sie es nicht speichern, wird das Paketupgrade temporär ausgeführt.<br /><br /> Die Skriptmigration eines [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Pakets wird dauerhaft ausgeführt, wenn Sie das Paket speichern. Wenn Sie es nicht speichern, wird das Paketupgrade temporär ausgeführt.|  
|Fügen Sie ein [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Paket zu einem vorhandenen Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] hinzu.|Das Paketupgrade ist dauerhaft. Bei einem [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paket ist die Skriptmigration dauerhaft.|  
|Öffnen Sie eine [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder eine [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]-Projektdatei in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], und aktualisieren Sie mehrere Pakete im Projekt mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] Paketupgrade-Assistenten.<br /><br /> Weitere Informationen finden Sie unter [Aktualisieren von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten](upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) und [SSIS Paketupgrade-Assistent (F1-Hilfe)](../ssis-package-upgrade-wizard-f1-help.md).|Das Paketupgrade ist dauerhaft. Bei einem [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paket ist die Skriptmigration dauerhaft.|  
|Verwenden Sie das Hilfsprogramm <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> -Methode, um ein oder mehrere [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete zu aktualisieren.|Das Paketupgrade ist dauerhaft. Bei einem [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paket ist die Skriptmigration dauerhaft.|  
  
## <a name="custom-applications-and-custom-components"></a>Benutzerdefinierte Anwendungen und benutzerdefinierte Komponenten  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] -Komponenten können nicht mit der aktuellen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Sie können die aktuelle Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Tools verwenden, um Pakete auszuführen und zu verwalten, die benutzerdefinierte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]- und [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]-Komponenten enthalten. Den folgenden Dateien wurden vier Bindungsumleitungsregeln hinzugefügt, um die Umleitung der Laufzeitassemblys von Version 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]) an Version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) zu erleichtern.  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 Verwendung von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] zum Entwerfen von Paketen, die enthalten [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] benutzerdefinierte Komponenten müssen Sie die Datei "devenv.exe.config" ändern, die unter  *\<Laufwerk >*: \programme\ Microsoft Visual Studio 10.0\Common7\IDE.  
  
 Zur Verwendung dieser Pakete mit Kundenanwendungen, die mit der Laufzeit für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erstellt werden, schließen Sie die Umleitungsregeln in den Konfigurationsabschnitt der Datei *.exe.config für die ausführbare Datei ein. Die Laufzeitassemblys werden durch die Regeln an Version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) umgeleitet. Weitere Informationen zur Umleitung von Assemblyversionen finden Sie unter [\<assemblyBinding>-Element für \<runtime>](https://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### <a name="locating-the-assemblies"></a>Suchen der Assemblys  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wurden die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Assemblys auf .NET 4.0 aktualisiert. Es ist ein separater globaler Assemblycache für .NET 4 verfügbar, der sich im Verzeichnis „*\<Laufwerk>*:\Windows\Microsoft.NET\assembly“ befindet. Normalerweise befinden sich alle [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Assemblys unter diesem Pfad im Ordner GAC_MSIL.  
  
 Wie bei früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befinden sich die zentralen DLL-Dateien für die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Erweiterbarkeit auch im Verzeichnis „*\<Laufwerk>*:\Programme\Microsoft SQL Server\100\SDK\Assemblies“.  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>Grundlegendes zu den Ergebnissen des SQL Server-Paketupgrades  
 Während des Paketupgrades werden die meisten Komponenten und Funktionen in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Paketen nahtlos in ihre Äquivalente der aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version konvertiert. Allerdings gibt es einige Komponenten und Funktionen, die entweder nicht aktualisiert werden oder zu Upgradeergebnissen führen, über die Sie sich im Klaren sein müssen. In der folgenden Tabelle werden diese Komponenten und Funktionen aufgeführt.  
  
> [!NOTE]  
>  Führen Sie Upgrade Advisor aus, um zu ermitteln, in welchen Paketen die in der Tabelle aufgeführten Probleme aufgetreten sind. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
|Komponente oder Funktion|Upgradeergebnisse|  
|--------------------------|---------------------|  
|Verbindungszeichenfolgen|Die Namen bestimmter Anbieter für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Pakete haben sich geändert und erfordern andere Werte in den Verbindungszeichenfolgen. Führen Sie zum Aktualisieren der Verbindungszeichenfolgen einen der folgenden Schritte aus:<br /><br /> Aktualisieren Sie das Paket mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketupgrade-Assistenten, und aktivieren Sie das Kontrollkästchen **Verbindungszeichenfolgen zum Verwenden neuer Anbieternamen aktualisieren**.<br /><br /> Aktivieren Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Dialogfeld „Optionen“ auf der Seite „Allgemein“ die Option **Verbindungszeichenfolgen mit neuen Anbieternamen aktualisieren**. Weitere Informationen zu dieser Option finden Sie unter [General Page](../general-page-of-integration-services-designers-options.md).<br /><br /> Öffnen Sie das Paket in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], und ändern Sie manuell den Text der ConnectionString-Eigenschaft.<br /><br /> Hinweis: Sie können nicht die vorherigen Prozeduren verwenden, um eine Verbindungszeichenfolge zu aktualisieren, wenn die Verbindungszeichenfolge in einer Konfigurationsdatei oder einer Datenquellendatei gespeichert wird, oder legt ein Ausdruck der `ConnectionString` Eigenschaft. Um die Verbindungszeichenfolge in diesen Fällen zu aktualisieren, müssen Sie die Datei oder den Ausdruck manuell aktualisieren.<br /><br /> Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen](../connection-manager/data-sources.md).|  
|Transformation für Suche|Bei [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paketen wird die Transformation für die Suche beim Upgrade automatisch auf die aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Version aktualisiert. Die aktuelle Version dieser Komponente bietet allerdings einige zusätzliche Funktionen, die Sie möglicherweise nutzen möchten.<br /><br /> Weitere Informationen finden Sie unter [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).|  
|Skripttask und Skriptkomponente|Beim Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Paketen werden Skripts im Skripttask und in der Skriptkomponente von VSA zu VSTA migriert.<br /><br /> Weitere Informationen zu Änderungen, die möglicherweise vor der Migration an Skripts vorgenommen werden müssen und zu Fehlern bei der Skriptkonvertierung führen, finden Sie unter [Migrieren von Skripts zu VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>Skripts, die von "ADODB.dll" abhängen  
 Skripttask- und Skriptkomponentenskripts, die explizit auf "ADODB.dll" verweisen, können auf Computern, auf denen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht installiert ist, weder aktualisiert noch ausgeführt werden. Zum Aktualisieren dieser Skripttask- und Skriptkomponentenskripts sollten Sie die Abhängigkeit auf „ADODB.dll“ entfernen.  Ado.Net ist die empfohlene Alternative für verwalteten Code, beispielsweise VB- und C#-Skripts.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Technischer Artikel [5 Tips for a Smooth SSIS Upgrade to SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=235321) (5 Tipps für ein nahtloses SSIS-Upgrade auf SQL Server 2012) auf „msdn.microsoft.com“.  
  
-   Blogeintrag [Making your Existing Custom SSIS Extensions and Applications Work in Denali](https://go.microsoft.com/fwlink/?LinkId=238157) (Weiterverwenden benutzerdefinierter SSIS-Erweiterungen und -Anwendungen in Denali) auf blogs.msdn.com.  
  
-   Webcast [Aktualisieren von SSIS-Paketen auf SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=258674) auf „channel9.msdn.com“.  
  
  
