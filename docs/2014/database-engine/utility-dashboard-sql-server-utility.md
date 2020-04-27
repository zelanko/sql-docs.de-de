---
title: Dashboard des Hilfsprogramms (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5f0eb497499eafe16756becfb9607b925add08e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62773812"
---
# <a name="utility-dashboard-sql-server-utility"></a>Dashboard des Hilfsprogramms (SQL Server-Hilfsprogramm)
  Um Daten im Dashboard des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramms anzuzeigen, wählen Sie den obersten Knoten in der Struktur des Hilfsprogramm-Explorers aus: Hilfsprogramm<UCP_Name>\\(ComputerName\UCP). Das Dashboard enthält Zusammenfassungs- und Detaildaten aus allen verwalteten Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und allen Datenebenenanwendungen im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm. Zum Aktualisieren der Dashboarddaten klicken Sie mit der rechten Maustaste auf den obersten Knoten in der Struktur des Hilfsprogramm-Explorers und wählen dann **Aktualisieren**aus.  
  
 Weitere Informationen zum Erstellen eines Steuerungspunkts für das Hilfsprogramm finden Sie unter [Erstellen eines Steuerungspunkts für das SQL Server-Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)aus. Weitere Informationen zum Hinzufügen einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm finden Sie unter [Registrieren einer Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)aus.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 Zustand der verwalteten Instanz  
 Der Zustand verwalteter Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wird links im Inhaltsbereich des Hilfsprogramm-Explorers angezeigt.  
  
 Die Zustandsparameter für verwaltete Instanzen lauten wie folgt:  
  
-   CPU-Auslastung für die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Auslastung der Datenbankdatei  
  
-   Speicherplatzauslastung auf Speichervolumes  
  
-   CPU-Auslastung für den Computer  
  
-   Der Status jedes Parameters ist in drei Kategorien unterteilt:  
  
-   Normal ausgelastet – Die Anzahl verwalteter Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die nicht gegen Richtlinien zur Ressourcennutzung verstoßen.  
  
-   Unterausgelastet – Die Anzahl verwalteter Ressourcen, die gegen Richtlinien zur Unterauslastung von Ressourcen verstoßen.  
  
-   Überausgelastet – Die Anzahl verwalteter Ressourcen, die gegen Richtlinien zur Überauslastung von Ressourcen verstoßen.  
  
-   Keine Daten verfügbar – Für verwaltete Instanzen von SQL Server sind keine Daten verfügbar, weil die Instanz von SQL Server entweder gerade erst registriert und der erste Datensammlungsvorgang noch nicht abgeschlossen wurde oder weil bei der verwalteten Instanz von SQL Server ein Problem im Hinblick auf die Sammlung und das Upload von Daten auf den UCP aufgetreten ist.  
  
 Der ausführliche Status für Zustandsparameter kann an verschiebbaren Indikatoren abgelesen werden. Der Teil rechts von den verschiebbaren Indikatoren zeigt an, wie viele verwaltete Instanzen sich in jeder Statuskategorie befinden.  
  
 Um eine gefilterte Sicht einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder einer Datenebenenanwendung zu erstellen, klicken Sie auf den Link für eine Auslastungskategorie neben dem entsprechenden verschiebbaren Indikator im Hilfsprogrammdashboard. Wenn Sie z. B. im Bereich **Inhalt des Hilfsprogramm-Explorers** auf **Überausgelastete Instanz-CPU** klicken, erstellt SSMS eine gefilterte Listenansicht von verwalteten Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die auf der Grundlage der aktuellen Richtlinieneinstellungen eine überausgelastete CPU haben.  
  
 Beachten Sie, dass der entsprechende Knoten im Hilfsprogramm-Explorer-Navigationsbereich mit **(gefiltert)** angefügt wird, wenn Sie auf einen Link für eine Auslastungskategorie klicken, d.h., **Verwaltete Instanzen** wird als **Verwaltete Instanzen (gefiltert)** bezeichnet. Um Filtereinstellungen anzuzeigen, klicken Sie mit der rechten Maustaste auf den Knoten im Navigationsbereich, wählen Sie **Filter**aus, und klicken Sie dann auf **Filtereinstellungen**. Um Filtereinstellungen zu löschen, klicken Sie mit der rechten Maustaste auf den Knoten im Navigationsbereich, wählen **Filter** aus und klicken dann auf **Filter entfernen**.  
  
 Weitere Informationen zum Anzeigen des Zustands einzelner Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bzw. zum Anzeigen oder Ändern der Einstellungen für die Richtlinienkonfiguration finden Sie unter [Details zu verwalteten Instanzen &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).  
  
 Hilfsprogrammzusammenfassung  
 Zeigt die Anzahl der verwalteten Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und die Anzahl der Datenebenenanwendungen an, die vom [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm verwaltet werden.  
  
 Zustand der Datenebenenanwendung  
 Der Zustand der Datenebenenanwendungen wird rechts im Inhaltsbereich des Hilfsprogramm-Explorers angezeigt.  
  
 Die Zustandsparameter für Datenebenenanwendungen lauten wie folgt:  
  
-   CPU-Auslastung für die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Auslastung der Datenbankdatei  
  
-   Speicherplatzauslastung auf Speichervolumes  
  
-   CPU-Auslastung für den Computer  
  
 Der Status jedes Parameters ist in drei Kategorien unterteilt:  
  
-   Normal ausgelastet – Die Anzahl der Datenebenenanwendungen, die nicht gegen Richtlinien zur Ressourcennutzung verstoßen.  
  
-   Überausgelastet – Die Anzahl der Datenebenenanwendungen, die gegen Richtlinien zur Überauslastung von Ressourcen verstoßen.  
  
-   Unterausgelastet – Die Anzahl der Datenebenenanwendungen, die gegen Richtlinien zur Unterauslastung von Ressourcen verstoßen.  
  
-   Keine Daten verfügbar – Für Datenebenenanwendungen sind keine Daten verfügbar, weil die verwaltete Instanz von SQL Server, die die Datenebenenanwendung enthält, keine Daten übermittelt.  
  
 Der ausführliche Status für Zustandsparameter kann an verschiebbaren Indikatoren abgelesen werden. Der Teil rechts neben den verschiebbaren Indikatoren zeigt an, wie viele Datenebenenanwendungen in jeder Statuskategorie enthalten sind. Weitere Informationen zum Anzeigen des Zustands einzelner Datenebenenanwendungen bzw. zum Anzeigen oder Ändern der Richtlinienkonfigurationseinstellungen finden Sie unter [Details zu bereitgestellten Datenebenenanwendungen &#40;SQL Server-Hilfsprogramm&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
 Verlauf der Auslastung des Hilfsprogrammspeichers  
 Der Verlauf der Auslastung wird in einem Zeitdiagramm unten im Dashboard des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramms angezeigt. Die Zeitangaben zeigen das lokale Datum und die lokale Uhrzeit des UCPs unter Verwendung des datetime-Datentyps an. Weitere Informationen finden Sie unter dem Thema [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) in der SQL Server-Onlinedokumentation. Beachten Sie bei Verwendung des Hilfsprogramm-Objektmodells, dass SSMS den datetimeoffset-Datentyp verwendet. Weitere Informationen finden Sie unter dem Thema [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) in der SQL Server-Onlinedokumentation.  
  
 Verwenden Sie die Optionsfelder links neben dem Anzeigebereich, um den Berichtszeitraum für das Diagramm zu ändern.  
  
 Die Optionen für das Berichtsintervall lauten:  
  
-   1 Tag, in Intervallen von 15 Minuten  
  
-   1 Woche, in Intervallen von 1 Tag  
  
-   1 Monat, in Intervallen von 1 Woche  
  
-   1 Jahr, in Intervallen von 1 Monat  
  
 Nachdem Sie eine Änderung am Berichtsintervall vorgenommen haben, werden die Daten automatisch aktualisiert.  
  
 Auslastung des Hilfsprogrammspeichers  
 Im Kreisdiagramm zur Speicherplatzauslastung unten rechts im Dashboard wird das Verhältnis von belegtem Speicherplatz zu freiem Speicherplatz auf Volumes angezeigt, die sich auf Computern mit verwalteten Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]befinden. Die Daten in dieser Anzeige werden alle 15 Minuten aktualisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des Hilfsprogramm-Explorers zum Verwalten des SQL Server-Hilfsprogramm](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Registrieren Sie eine Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)   
 [Ändern der Definition von Ressourcenintegritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
