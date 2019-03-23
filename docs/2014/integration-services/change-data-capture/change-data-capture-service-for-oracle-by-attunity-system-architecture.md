---
title: Change Data Capture Service für Oracle von Attunity System Architecture | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 84ac0e6065fa3fb4845e0e3a47ce56816705e80d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389398"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Change Data Capture Service für Oracle von Attunity System Architecture
  Der CDC Service for Oracle zeichnet Änderungen, die an ausgewählten Tabellen in einer oder mehreren Oracle-Quelldatenbanken vorgenommen werden, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC-Datenbanken auf einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz auf. Im folgenden Diagramm sind die Komponenten dargestellt, aus denen der CDC Service for Oracle besteht.  
  
 ![Dienstarchitektur](../media/service-architecture.gif "Dienstarchitektur")  
  
 Die Abbildung veranschaulicht die vier verwendeten Plattformen. In vielen Fällen können sich diese Plattformen überschneiden, aber dieses Diagramm zeigt einen standardmäßigen Anwendungsfall. Es ist z. B. sinnvoll, dass die Oracle- und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank jeweils auf einem separaten Computer ausgeführt werden und nicht gemeinsam mit der Oracle CDC Service-Plattform oder der Plattform genutzt werden, über die der CDC Service entworfen wird. In der Abbildung sind die folgenden Plattformen dargestellt:  
  
-   Der Oracle CDC Service: Dies kann einen beliebigen unterstützten Windows-Computer sein, in dem der Oracle CDC Service installiert und ausgeführt wird. Diese Plattform kann auch einen Clusterknoten in einem Microsoft-Failovercluster darstellen (Konfigurationen für Hochverfügbarkeit werden weiter unten in diesem Dokument behandelt).  
  
-   Der Oracle-Datenbank: Dies kann einem beliebigen Computer sein, bei dem eine unterstützte Version der Oracle-Datenbank ausgeführt wird. Dies gilt auch für Computer, auf denen Windows, Linux oder ein beliebiges anderes Betriebssystem ausgeführt wird, das von der installierten Version der Oracle-Datenbank unterstützt wird. Beachten Sie, dass diese Plattform im Diagramm im Plural angegeben ist, da ein einzelner Oracle CDC Service die Änderungen von mehreren Oracle-Quelldatenbanken aufzeichnen kann.  
  
-   Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Dies kann ein beliebiger Computer sein, in dem das Ziel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank (unterstützte SKU von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) ausgeführt wird. Ein Oracle CDC Service unterstützt ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ziel, auf dem dieser Änderungstabellen und die Dienstkonfiguration speichert. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Plattform kann auch eine gruppierte Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] oder eine gespiegelte Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] darstellen (mithilfe der **AlwaysOn** -Funktion).  
  
-   Oracle CDC Designer: Dies kann einen beliebigen unterstützten Windows-Computer, auf die Oracle-Quelldatenbank und das Ziel Zugriff sein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank.  
  
 In der folgenden Tabelle werden die Komponenten beschrieben, die auf den vier oben beschriebenen Plattformen ausgeführt werden.  
  
|Komponente/Beschreibung|Komponente besteht aus:|  
|----------------------------|----------------------------|  
|Oracle CDC-Dienst: Dies ist ein Windows-Dienst, in denen findet die Change Data Capture-Aktivität statt.|Oracle CDC-Instanz: Ein Unterprozess des Oracle CDC Service, Handles Data Capture-Aktivität für eine einzelne Oracle-Quelldatenbank zu ändern (es ist eine Oracle CDC-Instanz pro Oracle-Quelldatenbank).<br /><br /> Oracle Log Reader: Liest Oracle-Transaktionsprotokolle mithilfe des Oracle-Clients.<br /><br /> Oracle-Client: Den Oracle Instant Client für die Kommunikation mit Oracle verwendet. Dies ist eine erforderliche Komponente von Oracle, die vor dem Installieren des Oracle CDC Service vorhanden sein muss.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Change Writer: Schreibt per Commit ausgeführte Änderungen an der aufgezeichneten Oracle-Tabelle vorgenommen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Änderungstabellen. Diese Komponente behält diesen Aufzeichnungsstatus auch innerhalb der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Zieldatenbank bei.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ODBC-Client: Der Microsoft Native Client für [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Dies ist eine erforderliche Komponente von Microsoft, die vor dem Installieren des Oracle CDC Service vorhanden sein muss.|  
|Oracle CDC-Dienstkonfiguration: Dies ist ein Microsoft Management Console-Snap-in, die vom Windows-Dienst erstellt und seine Konfiguration festlegt.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client: Der SQL ADO.NET-Client, der in Version 4 von .NET Framework enthalten ist.|  
|Oracle-Datenbank: Eine Oracle-Quelldatenbank über die Änderungen an ausgewählten Tabellen werden erfasst.|Log Miner: Eine Oracle-Komponente, die über die Oracle-Transaktionsprotokolle gelesen werden.<br /><br /> Transaktionsprotokolle: Die online als auch archivierte Oracle Redo Logs, die von Oracle verwendet werden, um sicherzustellen, dass der Datenbank auszuführen, kann Transaktionen gesichert und wiederhergestellt werden (in diesem Fall die Oracle-Datenbank im Archivierungsprotokoll Modus betrieben werden muss).|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz: Ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz, auf die CDC-Datenbanken gehostet werden. Hierbei kann es sich um eine gruppierte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz (Failovercluster) oder eine gespiegelte Datenbank (AlwaysOn) handeln.|Die MSXDBCDC-Datenbank: Eine Datenbank, in dem Informationen über die CDC-Dienste, die Arbeit mit dieser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz bleibt. Darin sind auch Informationen zu den Oracle CDC-Instanzen enthalten, die von den einzelnen CDC Services behandelt werden. Diese Datenbank wird als Teil des CDC Service-Erstellungsprozesses angelegt.<br /><br /> CDC-Datenbanken: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbanken, in denen die in einer der Oracle-Quelldatenbanken vorgenommenen Änderungen gespeichert werden. Die CDC-Datenbanken sind für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC aktiviert, damit sie über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC-Tabellen und -Funktionen verfügen und von Oracle stammende Änderungen auf einfache Weise verarbeiten können.|  
|Oracle CDC Designer: Erstellen ein Microsoft Management Console-Snap-in, mit der Oracle CDC-Instanzen. Verwenden Sie es zum Auswählen der Tabellen und Spalten, die aufgezeichnet werden sollen, zum Bereitstellen von Oracle-Verbindungsinformationen und zum Verwalten des Lebenszyklus von CDC-Instanzen.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client: Der SQL ADO.NET-Client, der in Version 4 von .NET Framework enthalten ist.<br /><br /> Oracle-Client: Den Oracle Instant Client für die Kommunikation mit Oracle verwendet. Dies ist eine erforderliche Komponente von Oracle, die vor dem Installieren des Oracle CDC Service vorhanden sein muss.|  
  
 Der Oracle CDC Service und seine untergeordneten Oracle CDC-Instanzen können nur mit den Oracle-Quelldatenbanken und der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Zielinstanz als Clients kommunizieren. Damit werden nicht aktiv Netzwerke und andere Protokolle überwacht. Der Oracle CDC Service überwacht die CDC-Datenbanken auf Konfigurationsänderungen und passt seine Abläufe basierend auf der aktualisierten Konfiguration an.  
  
  
