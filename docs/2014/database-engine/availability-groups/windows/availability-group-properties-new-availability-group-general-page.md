---
title: Eigenschaften von Verfügbarkeits Gruppen und neue Verfügbarkeits Gruppe (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.general.f1
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 248ffe57906052c0d7dafcd187bb1b2b34cd6e64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62815653"
---
# <a name="availability-group-properties-and-new-availability-group-general-page"></a>„Eigenschaften der Verfügbarkeitsgruppe“ und „Neue Verfügbarkeitsgruppe“ (Seite „Allgemein“)
  Dieses Thema gilt für die Registerkarte **Allgemein** des Dialog Felds **neue Verfügbarkeits Gruppe** und des Dialog Felds **Eigenschaften der Verfügbarkeits Gruppe** .  Das Dialogfeld **Neue Verfügbarkeitsgruppe** ermöglicht es Ihnen, eine neue Verfügbarkeitsgruppe zu erstellen, ohne den [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]zu verwenden. Das Dialogfeld **Eigenschaften der Verfügbarkeitsgruppe** ermöglicht es Ihnen, die Konfiguration einer vorhandenen Verfügbarkeitsgruppe anzuzeigen und zu ändern.  
  
 **So zeigen Sie Verfügbarkeitsgruppeneigenschaften an**  
  
-   [Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)  
  
-   [Verwenden Sie das AlwaysOn-Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Name der Verfügbarkeits Gruppe**  
 Der Name der Verfügbarkeitsgruppe. Dies ist ein vom Benutzer angegebener Name, der innerhalb des Windows Server-Failoverclusters (WSFC) eindeutig sein muss.  
  
## <a name="availability-databases"></a>Verfügbarkeitsdatenbanken  
 **Database Name**  
 Name einer Datenbank, die der Verfügbarkeitsgruppe hinzugefügt wurde.  
  
 **Add (Hinzufügen)**  
 Klicken Sie, um der Verfügbarkeitsgruppe eine Datenbank hinzuzufügen.  
  
 **Remove**  
 Klicken Sie, um eine ausgewählte Datenbank aus der Verfügbarkeitsgruppe zu entfernen.  
  
## <a name="availability-replicas"></a>Verfügbarkeitsreplikate  
 **Server Instanz**  
 Entspricht dem Servernamen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz, die dieses Replikat hostet, sowie bei einer nicht standardmäßigen Instanz dem Instanznamen.  
  
 **Spielen**  
 **Primärer Server/verwaltete Instanz**  
 Derzeit das primäre Replikat.  
  
 **Secondary**  
 Derzeit ein sekundäres Replikat.  
  
 **Legen**  
 Die Replikatrolle wird derzeit zur primären oder sekundären Rolle aufgelöst.  
  
 **Verfügbarkeitsmodus**  
 Der Verfügbarkeitsmodus des Replikats. Folgende Werte sind möglich:  
  
 **Asynchroner Commit**  
 Das primäre Replikat kann einen Commit für Transaktionen ausführen, ohne das Schreiben des Protokolls auf den Datenträger durch das sekundäre Replikat abzuwarten.  
  
 **Synchroner Commit**  
 Das primäre Replikat wartet mit dem Ausführen des Commits für eine bestimmte Transaktion, bis das sekundäre Replikat die Transaktion auf den Datenträger geschrieben hat.  
  
 Weitere Informationen finden Sie unter [Verfügbarkeits Modi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md).  
  
 **Failovermodus**  
 Der Failovermodus des Replikats. Folgende Werte sind möglich:  
  
 **Automatisch**  
 Automatisches Failover. Das Replikat ist ein Ziel für automatische Failover. Diese Option wird nur unterstützt, wenn der Verfügbarkeitsmodus auf synchrone Commits festgelegt wird.  
  
 **Manuell**  
 Manuelles Failover. Ein Failover des Replikats kann nur manuell vom Datenbankadministrator ausgeführt werden.  
  
 **Verbindungen in primärer Rolle**  
 Der unterstützte Clientverbindungstyp, wenn das Replikat die primäre Rolle besitzt.  
  
 **Alle Verbindungen zulassen**  
 Für die Datenbanken im primären Replikat sind alle Verbindungen zugelassen. Dies ist die Standardeinstellung.  
  
 **Lese-/Schreibverbindungen zulassen**  
 Verbindungen, bei denen die Verbindungseigenschaft für die Anwendungsabsicht auf **ReadOnly** festgelegt ist, werden nicht zugelassen. Wenn die Eigenschaft für die Anwendungs Absicht auf "read **Write** " festgelegt ist oder die Verbindungs Eigenschaft für die Anwendungs Absicht nicht festgelegt ist, wird die Verbindung zugelassen. Weitere Informationen zur Verbindungseigenschaft für die Anwendungsabsicht finden Sie unter [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 **Lesbare sekundäre Datenbank**  
 Gibt an, ob ein Verfügbarkeitsreplikat, das die sekundäre Rolle ausführt (also einem sekundären Replikat entspricht), Verbindungen von Clients zulassen kann. Folgende Werte sind möglich:  
  
 **Nein**  
 Es werden keine direkten Verbindungen mit sekundären Datenbanken dieses Replikats zugelassen. Sie sind für den Lesezugriff nicht verfügbar. Dies ist die Standardeinstellung.  
  
 **Nur beabsichtigte Lesevorgänge**  
 Es sind nur direkte, schreibgeschützte Verbindungen mit sekundären Datenbanken dieses Replikats zulässig. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 **Ja**  
 Alle Verbindungen zu sekundären Datenbanken dieses Replikats sind zugelassen, aber nur für Lesezugriff. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 **Sitzungs Timeout (Sekunden)**  
 Die Anzahl der Sekunden für das Sitzungstimeout auf diesem Replikat.  
  
 **Endpunkt-URL**  
 Die URL des Endpunkts. Informationen über das Format dieser URLs finden Sie unter [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **Add (Hinzufügen)**  
 Klicken Sie, um ein sekundäres Replikat zur Verfügbarkeitsgruppe hinzuzufügen.  
  
 **Remove**  
 Klicken Sie, um ein sekundäres Replikat aus der Verfügbarkeitsgruppe zu entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
