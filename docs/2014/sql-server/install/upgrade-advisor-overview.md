---
title: Übersicht über den Upgrade Advisor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b3d10ff74c78e97ea554acdbcce3a5df0d76b74
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062391"
---
# <a name="upgrade-advisor-overview"></a>Übersicht über den Upgrade Advisor
  Upgrade Advisor stellt eine zentrale Konsole zum Analysieren der Komponenten von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und zum Anzeigen von Berichten bereit, die Informationen über die Analyseergebnisse enthalten.  
  
## <a name="how-upgrade-advisor-works"></a>Funktionsweise des Upgrade Advisors  
 Wenn Sie den Upgrade Advisor ausführen, wird die Startseite des Upgrade Advisors angezeigt. Die Startseite des Upgrade Advisors ist der Startpunkt für Folgendes:  
  
-   Analyse-Assistent des Upgrade Advisors  
  
-   Berichts-Viewer des Upgrade Advisors  
  
-   Hilfe zum Upgrade Advisor  
  
 Führen Sie bei der erstmaligen Verwendung des Upgrade Advisors den Analyse-Assistenten des Upgrade Advisors aus, um einen Server zu analysieren. Wenn der Assistent die Analyse abgeschlossen hat, klicken Sie im Assistenten auf **Bericht starten** , oder kehren Sie zur Startseite des Upgrade Advisors zurück. Führen Sie von dort aus den Berichts-Viewer des Upgrade Advisors aus, um den Bericht anzuzeigen. Der Bericht enthält Links zu Informationen, die Ihnen helfen, die bekannten Probleme zu beheben.  
  
## <a name="upgrade-advisor-analysis-wizard"></a>Analyse-Assistent des Upgrade Advisors  
 Um eine Analyse auszuführen, klicken Sie auf der Startseite des Upgrade Advisors auf **Upgrade Advisor-Analyse-Assistent starten** . Der Analyse-Assistent des Upgrade Advisors sammelt Informationen über den Computer, die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten und die Ablaufverfolgungsdateien, die analysiert werden sollen. Nachdem alle Informationen gesammelt und bestätigt wurden, analysiert der Analyse-Assistent des Upgrade Advisors die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten.  
  
> [!NOTE]  
>  Jedes Mal, wenn Sie den Analyse-Assistenten des Upgrade Advisors ausführen, wird ein separater Bericht generiert, und vorhandene Berichte für die ausgewählten Komponenten werden nicht überschrieben. Der Berichts-Viewer zeigt jedoch nur die letzten fünf Berichte an.  
  
 Wenn der Analyse-Assistent des Upgrade Advisors seine Analyse beendet, erstellt er eine XML-Datei für jede Komponente, die Sie in die Analyse einbezogen haben. Die Elemente und Probleme, die in jeder Komponente ermittelt werden, sind in den XML-Dateien enthalten.  
  
### <a name="what-upgrade-advisor-analyzes"></a>Vom Upgrade Advisor analysierte Elemente  
 Für jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponente wird im Kontext des Upgrade Advisors eine dedizierte Analyse ausgeführt. Bei jeder Analyse wird ein XML-Bericht für die jeweilige Komponente ausgegeben.  
  
 Der Upgrade Advisors fragt die folgenden Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab:  
  
-   Datenbankserver (in der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Onlinedokumentation auch als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bezeichnet), worin Replikation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent, Volltextsuche und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client einbezogen sind  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  Während der Analyse erstellt jeder Analyzer eine Protokolldatei. Sie können diese Protokolldateien verwenden, um die bei der Analyse aufgetretenen Fehler zu beheben. Wenn der Upgrade Advisor z. B. langsam ausgeführt wird, können Sie die Ursache der Verzögerung anhand der Protokolldateien feststellen.  
  
### <a name="upgrade-advisor-limitations"></a>Einschränkungen des Upgrade Advisors  
 Der Upgrade Advisor erkennt nicht jedes Problem, das ein Upgrade beeinflussen könnte. Wenn eine auf Desktops von Endbenutzern ausgeführte Clientanwendung beispielsweise eingebetteten SQL-Code enthält, kann der Upgrade Advisor die Anwendungen nicht analysieren. Sie müssen die Probleme für diese Elemente berücksichtigen und die Informationen entsprechend der Installation aktualisieren, migrieren oder ändern.  
  
 Der Upgrade Advisor analysiert keine verschlüsselten gespeicherten Prozeduren, keinen Code in erweiterten gespeicherten Prozeduren sowie keinen Quellcode in anderen Sprachen als [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="upgrade-advisor-report-viewer"></a>Berichts-Viewer des Upgrade Advisors  
 Um einen Upgrade Advisor-Bericht anzuzeigen, klicken Sie auf der Startseite des Upgrade Advisors auf **Upgrade Advisor Report Viewer starten** . Wenn der Berichts-Viewer des Upgrade Advisors gestartet wird, werden die Berichte im Standardverzeichnis geladen. Berichte werden nicht angezeigt, wenn der Berichts-Viewer des Upgrade Advisors keine Berichte im Standardverzeichnis findet. Wenn das Standardverzeichnis keine Berichte enthält, können Sie entweder den Analyse-Assistenten des Upgrade Advisors ausführen, um einen Bericht zu erstellen, oder einen vorhandenen Bericht eines anderen Servers oder Unterverzeichnisses laden.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor überschreibt keine vorhandenen Berichte. Der Berichts-Viewer zeigt jedoch nur die letzten fünf Berichte an. Um einen früheren Bericht anzuzeigen, wählen Sie den Bericht im Dropdown-Listenfeld **Bericht** aus. Der Zeitstempel gibt das Datum und die Uhrzeit an, an denen der Bericht generiert wurde.  
  
 Wenn XML-Dateien aus dem Analyse-Assistenten des Upgrade Advisors in den Berichts-Viewer des Upgrade Advisors geladen werden, wird für jede Komponente ein Bericht angezeigt. Der Bericht enthält alle bekannten Probleme, d. h. sowohl die auffindbaren als auch die nicht auffindbaren Probleme, die Sie beheben müssen. Für jedes Problem gibt es ein Symbol zur Angabe der Wichtigkeit, eine Bezeichnung, die Sie über den Zeitpunkt der Problembehebung informiert, und eine kurze Beschreibung. Wenn Sie ein Problem erweitern, sehen Sie ein längere Beschreibung, einen Link zu Problemdetails und einen Link zur Hilfedatei. Die Angaben für jedes Problem bieten genug Informationen, um das Problem beheben zu können.  
  
 Bei den meisten Komponenten gibt es Probleme, die nicht erkannt werden können. Um diese Probleme anzuzeigen, erweitern Sie das Element **andere Upgradeprobleme** für die Komponente, und klicken Sie dann auf den Link, um weitere Informationen zu den Problemen in der Dokumentation anzuzeigen. Weitere Informationen zu Problemen mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abwärtskompatibilität finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
