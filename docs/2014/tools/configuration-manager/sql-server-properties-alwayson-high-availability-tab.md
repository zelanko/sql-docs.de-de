---
title: SQL Server Eigenschaften (Registerkarte "hohe Verfügbarkeit" von AlwaysOn) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die AlwaysOn-Verfügbarkeitsgruppen Funktion in SQL Server 2014 aktivieren oder deaktivieren. Anzeige Voraussetzungen anzeigen, die die Serverinstanz für dieses Feature erfüllen muss.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: cc145da0b6296d3f6e048905e4ab4e649294d38a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048488"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a>SQL Server-Eigenschaften (Registerkarte Hohe Verfügbarkeit (immer aktiviert))
  Verwenden Sie die Registerkarte **Hohe Verfügbarkeit (immer aktiviert)** des Dialogfelds **SQL Server-Eigenschaften** im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um die Funktion AlwaysOn-Verfügbarkeitsgruppen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]zu aktivieren oder zu deaktivieren. Die Aktivierung von AlwaysOn-Verfügbarkeitsgruppen ist eine Voraussetzung dafür, dass eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz Verfügbarkeitsgruppen als Lösung für Hochverfügbarkeit und Notfallwiederherstellung verwenden kann.  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Damit eine Serverinstanz für AlwaysOn-Verfügbarkeitsgruppen aktiviert werden kann, muss sie die folgenden Voraussetzungen erfüllen:  
  
-   Die Serverinstanz muss sich auf einem WSFC-Knoten (Windows Server Failover Clustering) befinden.  
  
-   Instanzen müssen sich im gleichen WSFC-Cluster befinden, damit sie derselben Verfügbarkeitsgruppe angehören. Eine Verfügbarkeitsgruppe kann sich nicht über mehrere WSFC-Cluster erstrecken.  
  
-   Auf der Serverinstanz muss eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Edition mit [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]-Unterstützung ausgeführt werden.  
  
-   AlwaysOn-Verfügbarkeitsgruppen sollten jeweils nur für eine Serverinstanz aktiviert werden. Warten Sie nach der Aktivierung von AlwaysOn-Verfügbarkeitsgruppen, bis der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst neu gestartet wurde, bevor Sie die nächste Serverinstanz aktivieren.  
  
> [!NOTE]  
>  Informationen zur Funktionsunterstützung sowie zu zusätzlichen Voraussetzungen, Einschränkungen und Empfehlungen zu [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]finden Sie in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Onlinedokumentation.  
  
## <a name="dialog-options"></a>Dialogfeldoptionen  
 **Name des Windows-Failoverclusters**  
 Zeigt den Namen des WSFC-Clusters an, in dem der lokale Computer einen Knoten darstellt.  
  
 **AlwaysOn-Verfügbarkeitsgruppen aktivieren**  
 Verwenden Sie dieses Kontrollkästchen, um AlwaysOn-Verfügbarkeitsgruppen auf dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz wie folgt zu aktivieren oder deaktivieren:  
  
-   Wenn dieses Kontrollkästchen leer ist, sind AlwaysOn-Verfügbarkeitsgruppen derzeit deaktiviert. Aktivieren Sie dieses Kontrollkästchen, um AlwaysOn-Verfügbarkeitsgruppen zu aktivieren, klicken Sie auf **OK**, und starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst manuell erneut.  
  
-   Wenn dieses Kontrollkästchen bereits aktiviert ist, sind AlwaysOn-Verfügbarkeitsgruppen derzeit aktiviert. Um AlwaysOn-Verfügbarkeitsgruppen zu deaktivieren, deaktivieren Sie das Kontrollkästchen und klicken auf **OK**. Dadurch wird die Serverinstanz neu gestartet.  
  
    > [!TIP]  
    >  Nach der Deaktivierung von AlwaysOn-Verfügbarkeitsgruppen sollten Sie alle lokalen Verfügbarkeitsreplikate aus der Serverinstanz entfernen. Nachdem Sie das letzte Replikat einer bestimmten Verfügbarkeitsgruppe entfernt haben, sollten Sie auch die Gruppe entfernen.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
  
> [!NOTE]  
>  Weitere Informationen zu den Schritten, die im Anschluss an die Deaktivierung von AlwaysOn-Verfügbarkeitsgruppen erforderlich sind, sowie Informationen zum Erstellen und Konfigurieren von Verfügbarkeitsgruppen finden Sie in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Onlinedokumentation.  
  
  
