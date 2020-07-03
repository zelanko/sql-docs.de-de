---
title: Konzepte der Data Quality Services
ms.date: 01/01/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 837c71ee-48fa-4044-8744-2be9119aaa04
author: swinarko
ms.author: sawinark
ms.openlocfilehash: fe7f6c957bb1781528c0bad06de41063c41ca3cc
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887948"
---
# <a name="data-quality-services-concepts"></a>Konzepte der Data Quality Services

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Dieses Thema enthält eine kurze Zusammenfassung der [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)-Konzepte in Wissensverwaltung, Data Quality-Projekten und Datenqualitätsverwaltung.  
  
##  <a name="knowledge-management-concepts"></a><a name="Knowledge"></a> Konzepte der Wissensverwaltung  
 Die DQS-Wissensdatenbank ist ein Repository von Metadaten, die vom Data Steward oder IT-Profi zur Verwendung bei der Verbesserung der Datenqualität durch Datenbereinigung und Datenabgleich erstellt werden. Die DQS-Wissensverwaltung schließt die Prozesse ein, die verwendet wurden, um die Wissensdatenbank zu erstellen und zu verwalten, sowohl in einer computergestützten Weise als auch interaktiv.  
  
 **Wissens Ermittlung**  
  
 Die Wissensermittlung ist ein computergestützter Prozess, der Beispiele für die Daten der Organisation analysiert, um Wissen zu den Daten zu erstellen. Sobald die Ergebnisse der Analyse vorliegen, können Sie das Wissen überprüfen und verbessern und es dann auf die Durchführung von Datenbereinigungen, den Datenabgleich und die Profilerstellung anwenden. Weitere Informationen finden Sie unter [DQS Knowledge Bases and Domains](../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Domänen Verwaltung**  
  
 Der Domänenverwaltungsprozess ermöglicht es Ihnen, das Wissen zu ändern, das vom Wissensermittlungsprozess generiert wurde, oder es zu erweitern. Sie können das Wissen in einer Wissensdatenbank interaktiv bearbeiten, aktualisieren und überprüfen. Eine Wissensdatenbank besteht aus Datendomänen, die Domänenwerte und ihren Status, Domänenregeln, begriffsbasierte Beziehungen und Verweisdaten enthalten. In der Domänenverwaltung können Sie Domäneneigenschaften ändern, Verweisdaten an eine Domäne anfügen, Domänenregeln verwalten, Domänenwerte verwalten und Datenbeziehungen eingeben sowie Domänen erstellen, löschen, importieren oder exportieren. Sie können auch Verbunddomänen verwenden, die mehr als eine einzelne Domäne aggregieren. Weitere Informationen finden Sie unter [DQS Knowledge Bases and Domains](../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Übereinstimmende Richtlinie**  
  
 Eine Abgleichsrichtlinie enthält die Abgleichsregeln, die verwendet werden, um Datendeduplizierung auszuführen. Der Abgleichsrichtlinienprozess ermöglicht es Ihnen, Abgleichsregeln zu erstellen, sie basierend auf Abgleichsergebnissen und Profilerstellungsdaten anzupassen und der Wissensdatenbank die Richtlinie hinzuzufügen. Weitere Informationen finden Sie unter [Data Matching](../data-quality-services/data-matching.md).  
  
 **Reference Data Services**  
  
 Sie können Verweisdaten verwenden, um die Daten zu überprüfen, zu korrigieren und anzureichern und dabei die Dienste von Unternehmen nutzen, die die Qualität ihrer Verweisdaten garantieren. Sie können die Dienste von Azure Marketplace verwenden, um eine Verbindung mit Verweis Datenanbietern herzustellen, oder Sie können eine direkte Verbindung zu einem Anbieter verwenden. Weitere Informationen finden Sie unter [Reference Data Services in DQS](../data-quality-services/reference-data-services-in-dqs.md).  
  
 Weitere Informationen zur Wissensverwaltung in DQS finden Sie unter [DQS Knowledge Bases and Domains](../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
##  <a name="data-quality-project-concepts"></a><a name="Projects"></a> Konzepte des Data Quality-Projekts  
 Der Data Steward führt Data Quality-Vorgänge (Bereinigung und Abgleich) mithilfe eines Data Quality-Projekts in der Anwendung [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] aus.  
  
 **Datenbereinigung**  
  
 Die Datenbereinigung in DQS wird auf Grundlage des Wissens in einer DQS-Wissensdatenbank ausgeführt. Die Datenbereinigung in DQS umfasst zwei Schritte:  
  
-   **Computergestützte Bereinigung**: DQS verwendet das Wissen in der ausgewählten Wissensdatenbank für das Bereinigungsprojekt, um Korrekturen/Vorschläge für die Werte in einer Datenquelle anzubieten.  
  
-   **Interaktive Bereinigung**: Der Data Steward kann den interaktiven Bereinigungsprozess ausführen, um Datenkorrekturen, die vom computergestützten Datenbereinigungsprozess vorgeschlagen wurden, zu ändern oder zu erweitern. Der Data Steward verwendet dabei Vertrauensgrade und Statistiken, die vom Datenbereinigungsprozess identifiziert werden, oder eigene Änderungen, die manuell in das Projekt eingegeben werden.  
  
 Der Data Steward kann die verarbeiteten Daten nach der Bereinigung in eine SQL Server-Datenbank, CSV- oder Excel-Datei exportieren. Weitere Informationen finden Sie unter [Data Cleansing](../data-quality-services/data-cleansing.md).  
  
 **Datenabgleich**  
  
 Der Abgleichsprozess ermöglicht es dem Data Steward, Daten abzugleichen, damit ähnliche, aber leicht abweichende Daten anhand eines Deduplizierungsprozesses ausgerichtet werden können. DQS führt die Deduplizierung auf Grundlage der in der Wissensdatenbank enthaltenen Abgleichsregeln aus; die Parameter für den Abgleichsprozess werden vom Data Steward aus dem Data Quality-Projekt heraus angegeben. Weitere Informationen finden Sie unter [Data Matching](../data-quality-services/data-matching.md).  
  
 **Profilerstellung und Benachrichtigungen**  
  
 Die Datenprofilerstellung stellt Data Stewards während der Ausführung eines Data Quality-Projekts Statistiken und Informationen zu den von DQS verarbeiteten Daten in Echtzeit bereit, die für Bereinigungs- und Abgleichsaktivitäten verwendet werden. Mithilfe der Datenprofilerstellung können Sie die Effektivität der Bereinigungs- und Abgleichsprozesse in einem Data Quality-Projekt bewerten. Außerdem unterstützen Benachrichtigungen den Benutzer bei Aktionen, die zur Verbesserung der Datenbereinigungs- und Datenabgleichsvorgänge ausgeführt werden können. Weitere Informationen finden Sie unter [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md).  
  
 Weitere Informationen zu Data Quality-Projekten in DQS finden Sie unter [Data Quality-Projekte &#40;DQS&#41;](../data-quality-services/data-quality-projects-dqs.md).  
  
##  <a name="data-quality-administration-concepts"></a><a name="Admin"></a> Konzepte der Data Quality-Verwaltung  
 Ein DQS-Administrator kann eine Vielzahl von administrativen Aufgaben mithilfe der Anwendung [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ausführen.  
  
 **Aktivitäts Überwachung**  
  
 Die Aktivitätsüberwachung zeigt den Status und den Zustand jeder Aktivität an, die innerhalb eines Datenbereichs durchgeführt wird, stellt Daten für jede Aktivität bereit und ermöglicht es DQS-Administratoren, eine Aktivität zu steuern. Weitere Informationen finden Sie unter [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
 **Configuration**  
  
 Die Option "Konfiguration" bietet folgende Möglichkeiten:  
  
-   Konfigurieren der Einstellungen für den Reference Data Service. Weitere Informationen finden Sie unter [Configure DQS to Use Reference Data](../data-quality-services/configure-dqs-to-use-reference-data.md).  
  
-   Festlegen der Schwellenwerte für die Bereinigungs- und Abgleichsaktivitäten. Weitere Informationen finden Sie unter [Konfigurieren der Schwellenwerte für Bereinigung und Abgleich](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   Aktivieren/Deaktivieren von Profilerstellungsbenachrichtigungen. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren von Profilerstellungsbenachrichtigungen in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md).  
  
-   Konfigurieren der Schweregradeinstellungen für die DQS-Protokolldateien auf der aktivitätsbasierten Ebene oder der erweiterten modulbasierten Ebene. Weitere Informationen finden Sie unter [Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md).  
  
 **DQS-Sicherheit**  
  
 Sie verwenden Rollen innerhalb des SQL Server-Sicherheitsmechanismus, um DQS sicher zu machen. Es gibt drei DQS-Rollen, die die Zugriffsebene für einen Benutzer in der Anwendung [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] bestimmen: dqs_administrator, dqs_kb_editor und dqs_kb_operator. Mithilfe der Anwendung [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] können Sie den Benutzern keine Rollen gewähren; dazu verwenden Sie SQL Server Management Studio. Weitere Informationen finden Sie unter [DQS Security](../data-quality-services/dqs-security.md).  
  
 Weitere Informationen zur DQS-Verwaltung finden Sie unter [DQS Administration](../data-quality-services/dqs-administration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Quality Services](../data-quality-services/data-quality-services.md)  
  
  
