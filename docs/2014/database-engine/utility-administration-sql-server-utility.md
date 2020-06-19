---
title: Hilfsprogrammverwaltung (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fca4ea655ffdcf8471d1340016d16f2c5b9c352a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927671"
---
# <a name="utility-administration-sql-server-utility"></a>Hilfsprogrammverwaltung (SQL Server-Hilfsprogramm)
  Verwenden Sie die Registerkarten der Hilfsprogrammverwaltung zum Verwalten von Richtlinien-, Sicherheits- und Data Warehouse-Einstellungen für ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm. Weitere Informationen zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogrammkonzepten finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 Registerkarte Richtlinie – Verwenden Sie die Registerkarte Richtlinie, um globale Überwachungsrichtlinien anzuzeigen oder anzugeben.  
  
 Legen Sie globale Überwachungsrichtlinien für Datenebenenanwendungen fest. Um die Werteliste für diese Option zu erweitern, klicken Sie neben dem Richtliniennamen auf den Pfeil, oder klicken Sie auf den Richtlinientitel.  
 Wann wird die Prozessorkapazität für eine Anwendung knapp? Zum Ändern dieser Richtlinie verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Prozessorauslastung beträgt 70 %.  
  
-   Der minimale Standardwert für die Prozessorauslastung beträgt 0 %.  
  
 Wann wird der Dateispeicherplatz für eine Anwendung knapp? Um die Richtlinie zur Speicherplatzauslastung einer Daten- oder Protokolldatei zu ändern, verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Auslastung des Dateispeicherplatzes beträgt 70 %.  
  
-   Der minimale Standardwert für die Auslastung des Dateispeicherplatzes beträgt 0 %.  
  
 Legen Sie globale Überwachungsrichtlinien für verwaltete Instanzen von SQL Server fest. Um die Werteliste für diese Option zu erweitern, klicken Sie neben dem Richtliniennamen auf den Pfeil, oder klicken Sie auf den Richtlinientitel.  
 Wann wird die Prozessorkapazität für eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] knapp? Zum Ändern dieser Richtlinie verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Prozessorauslastung von Instanzen beträgt 70 %.  
  
-   Der minimale Standardwert für die Prozessorauslastung von Instanzen beträgt 0 %.  
  
 Wann wird die Prozessorkapazität auf einem Computer mit einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] knapp? Zum Ändern dieser Richtlinie verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Prozessorauslastung von Computern beträgt 70 %.  
  
-   Der minimale Standardwert für die Prozessorauslastung von Computern beträgt 0 %.  
  
 Wann wird der Dateispeicherplatz für eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] knapp? Um die Richtlinie zur Speicherplatzauslastung einer Daten- oder Protokolldatei zu ändern, verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Auslastung des Dateispeicherplatzes beträgt 70 %.  
  
-   Der minimale Standardwert für die Auslastung des Dateispeicherplatzes beträgt 0 %.  
  
 Wann wird die Speichervolumekapazität auf einem Computer mit einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] knapp? Zum Ändern dieser Richtlinie verwenden Sie das Steuerelement rechts neben der Richtlinienbeschreibung, und klicken Sie auf **Anwenden**. Mithilfe der Schaltflächen unten in der Anzeige können Sie auch Standardwerte wiederherstellen oder Änderungen verwerfen.  
  
-   Der maximale Standardwert für die Auslastung des Volumespeicherplatzes auf einem Computer beträgt 70 %.  
  
-   Der minimale Standardwert für die Auslastung des Volumespeicherplatzes auf einem Computer beträgt 0 %.  
  
 Reduzieren von Informationsrauschen aufgrund von Richtlinienverstößen bei stark veränderlichen Ressourcen. Um weitere Steuerelemente für diese Funktion anzuzeigen, klicken Sie rechts in der Anzeige auf den nach unten weisenden Pfeil.  
 Weitere Informationen finden Sie unter [reduzieren von Rauschen in Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 Registerkarte Sicherheit – Zeigt Anmeldenamen mit Berechtigungen zum Verwalten oder Lesen von Informationen aus dem UCP an.  
  
 Wählen Sie die Anmeldenamen aus dem UCP aus, die der Hilfsprogrammleser-Rolle hinzugefügt werden.  
 Die Hilfsprogrammleser-Berechtigung ermöglicht folgende Aktionen unter dem Benutzerkonto:  
  
-   Herstellen einer Verbindung mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm  
  
-   Anzeigen aller Blickpunkte im Hilfsprogramm-Explorer in SSMS  
  
-   Anzeigen der Einstellungen im Knoten Hilfsprogrammverwaltung im Hilfsprogramm-Explorer in SSMS  
  
 Hilfsprogrammadministratoren können SQL Server-Instanzen registrieren und SQL Server-Instanzen aus einem SQL Server-Hilfsprogramm entfernen sowie Richtlinien für verwaltete Instanzen und Verwaltungseinstellungen für den UCP ändern.  
  
 Als Hilfsprogrammadministrator müssen Sie über sysadmin-Berechtigungen für die SQL Server-Instanz verfügen. Um Benutzerkonten für den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-UCP hinzuzufügen oder zu ändern, fügen Sie dem Benutzer mithilfe des Objekt-Explorers in SSMS Serveranmeldenamen der UCP-Instanz von SQL Server hinzu. Weitere Informationen finden Sie unter [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 Registerkarte Data Warehouse – Zeigt Konfigurationsdetails für das UMDW (Utility Management Data Warehouse) an.  
  
 Datenaufbewahrung  
 Geben Sie die Beibehaltungsdauer von Auslastungsdaten an, die für verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]gesammelt wurden. Der Standardzeitraum beträgt ein Jahr. Der Minimalwert beträgt einen Monat. Der längste unterstützte Wert beträgt zwei Jahre.  
  
 Konfigurationsinformationen für das Hilfsprogramm-Data Warehouse  
 Die folgenden Konfigurationseinstellungen sind in dieser Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht konfigurierbar:  
  
-   Umschlag Name: Sysutility_mdw_ \<GUID> _data.  
  
-   Uploadfrequenz für den Sammlungssatz: Alle 15 Minuten  
  
 Das Verzeichnis "verdw" ist konfigurierbar: \<System drive> : \Programme\Microsoft SQL Server \ MSSQL10_50. <UCP_Name> \MSSQL\Data \\ , wobei \<System drive> normalerweise C:\ ist. Antrie. Die Protokolldatei, UMDW_ \<GUID> _log, befindet sich im gleichen Verzeichnis.  
  
> [!NOTE]  
>  Der Speicherort der UMDW-Datei (sysutility_mdw) kann mithilfe von Detach/Attach oder ALTER DATABASE geändert werden. Es wird empfohlen, ALTER DATABASE zu verwenden. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
 Wiederherstellen vordefinierter Standardwerte  
 Um die Einstellungen auf dieser Registerkarte auf die Standardwerte zurückzusetzen, klicken Sie auf die Schaltfläche **Standardwerte wiederherstellen** und anschließend auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Hilfsprogramm des Utility-Dashboards &#40;&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Details zu bereitgestellten Datenebenenanwendungen &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)   
 [Verwaltete Instanz Details &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)   
 [Überwachen von SQL Server-Instanzen im SQL Server-Hilfsprogramm](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  
