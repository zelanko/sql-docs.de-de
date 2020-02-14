---
title: Websynchronisierung für die Mergereplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication synchronization [SQL Server replication]
- Internet [SQL Server replication], synchronization
- synchronization [SQL Server replication], Web Synchronization
- Web publishing [SQL Server replication], synchronization
- Web synchronization, about
- Web synchronization
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db49332ec2710586e9cae23c3e41ee4aff42b486
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68136968"
---
# <a name="web-synchronization-for-merge-replication"></a>Websynchronisierung für die Mergereplikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Durch die Websynchronisierung für die Mergereplikation können Sie Daten mithilfe des HTTPS-Protokolls replizieren. Sie ist für die folgenden Szenarien hilfreich:  
  
-   Synchronisieren von Daten mobiler Benutzer über das Internet.  
  
-   Synchronisieren von Daten zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken über eine Unternehmensfirewall hinweg.  
  
 Ein Außendienstmitarbeiter kann z. B. die Websynchronisierung verwenden. Einige Vertriebsmitarbeiter des Unternehmens, [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], besuchen verschiedene Geschäfte und Lieferanten in ihren jeweiligen Regionen. Bei längeren Reisen übernachten die Mitarbeiter in Hotels und benötigen am Ende jeden Tages eine praktische Möglichkeit zum Hochladen der Verkaufsdaten und Herunterladen eventueller Produktupdates.  
  
 Die IT-Abteilung von [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] hat jeden Laptop mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfiguriert und die Mergereplikation für die Verwendung der Websynchronisierung aktiviert. Der Merge-Agent auf jedem Laptop verfügt über eine Internet-URL. Diese URL verweist auf die Replikationskomponenten, die auf einem Computer mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS (Internet Information Services) installiert sind. Diese Komponenten synchronisieren den Abonnenten mit dem Verleger. Jeder Mitarbeiter kann nun über jede verfügbare Internetverbindung ohne Verwendung einer Remote-DFÜ-Verbindung eine Verbindung herstellen und die entsprechenden Daten hoch- und herunterladen. Die Internetverbindung verwendet SSL (Secure Sockets Layer). Somit ist kein virtuelles privates Netzwerk (VPN) erforderlich.  
  
 Informationen zum Konfigurieren der für die Websynchronisierung erforderlichen Komponenten finden Sie unter [Konfigurieren der Websynchronisierung](../../relational-databases/replication/configure-web-synchronization.md), [Konfigurieren von IIS für die Websynchronisierung](../../relational-databases/replication/configure-iis-for-web-synchronization.md) und[Konfigurieren von IIS 7 für die Websynchronisierung](../../relational-databases/replication/configure-iis-7-for-web-synchronization.md).  
  
> [!NOTE]  
>  Die Websynchronisierung ist für die Synchronisierung von Daten mit Laptops, Handhelds und anderen Clients entwickelt worden. Sie eignet sich nicht für Server-zu-Server-Anwendungen für hohes Volumen.  
  
## <a name="overview-of-how-web-synchronization-works"></a>Funktionsweise der Websynchronisierung (Übersicht)  
 Wenn die Websynchronisierung verwendet wird, werden Updates auf dem Abonnenten verpackt und als XML-Nachricht mit dem HTTPS-Protokoll an den Computer mit IIS gesendet. Der Computer mit IIS sendet dann die Befehle in einem Binärformat (in der Regel mit TCP/IP) an den Verleger. Updates auf dem Verleger werden an den Computer mit IIS gesendet und dann als XML-Nachricht zur Übermittlung an den Abonnenten verpackt.  
  
 Die folgende Abbildung zeigt einige Komponenten der Websynchronisierung für die Mergereplikation.  
  
 ![Komponenten und Datenfluss für die Websynchronisierung](../../relational-databases/replication/media/web-sync01.gif "Komponenten und Datenfluss für die Websynchronisierung")  
  
 Die Websynchronisierung steht nur für Pullabonnements zur Verfügung. Ein Merge-Agent wird deshalb immer auf dem Abonnenten ausgeführt. Dabei kann es sich um den Standard-Merge-Agent, das ActiveX-Steuerelement für den Merge-Agent oder eine Anwendung handeln, die die Synchronisierung über Replikationsverwaltungsobjekte (RMO) bereitstellt. Mit dem **–InternetUrl** -Parameter für den Merge-Agent wird der Standort des Computers mit IIS angegeben.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikationsüberwachung (Replisapi.dll) ist auf dem Computer mit IIS konfiguriert und verarbeitet die Nachrichten, die vom Verleger und den Abonnenten an den Server gesendet werden. Jeder Knoten in der Topologie verarbeitet den XML-Datenstrom mithilfe der SQL Server-Mergereplikationssynchronisierung (Replrec.dll).  
  
 Für alle Computer, die an einer Websynchronisierung teilnehmen, ist[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder eine höhere Version erforderlich.  
  
### <a name="synchronization-process"></a>Synchronisierungsvorgang  
 Die folgenden Schritte erfolgen bei der Synchronisierung:  
  
1.  Der Merge-Agent wird auf dem Abonnenten gestartet. Dieser Agent führt die folgenden Aufgaben aus:  
  
    1.  Herstellen einer SQL-Verbindung zur Abonnementdatenbank.  
  
    2.  Extrahieren von Änderungen aus der Datenbank.  
  
    3.  Ausführen einer HTTPS-Anforderung an den Computer mit IIS.  
  
    4.  Hochladen von Datenänderungen als XML-Nachricht.  
  
2.  Die Komponenten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikationsüberwachung und -Mergereplikationssynchronisierung, die auf dem Computer mit IIS gehostet werden, führen die folgenden Aufgaben aus:  
  
    1.  Antworten auf die HTTPS-Anforderung.  
  
    2.  Herstellen einer SQL-Verbindung zur Veröffentlichungsdatenbank.  
  
    3.  Anwenden der Uploadänderungen auf die Veröffentlichungsdatenbank.  
  
    4.  Extrahieren der Downloadänderungen für den Abonnenten.  
  
    5.  Zurücksenden einer HTTPS-Antwort an den Merge-Agent.  
  
3.  Der Merge-Agent auf dem Abonnenten akzeptiert anschließend die HTTPS-Antwort und wendet die Downloadänderungen auf die Abonnementdatenbank an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Websynchronisierung](../../relational-databases/replication/configure-web-synchronization.md)   
 [Topologien für die Websynchronisierung](../../relational-databases/replication/topologies-for-web-synchronization.md)  
  
  
