---
title: Source-Control-Grundlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], providers
- source controls [SQL Server Management Studio]
- source controls [SQL Server Management Studio], about source controls
- source controls [SQL Server Management Studio], clients
ms.assetid: ca35b67a-104a-41fb-ac58-a61be06fe114
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d6ff97973a1e3d34d3e6601b9bb14f9edc4c4abd
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43816326"
---
# <a name="source-control-basics"></a>Grundlagen zur Quellcodeverwaltung
  Die Quellcodeverwaltung steht für ein System, in dem eine Serversoftware Dateiversionen speichert und nachverfolgt sowie den Zugriff auf Dateien steuert. Ein typisches Quellcodeverwaltungssystem enthält einen Quellcodeverwaltungsanbieter und zwei oder mehr Quellcodeverwaltungsclients.  
  
## <a name="source-control-benefits"></a>Vorteile der Quellcodeverwaltung  
 Platzieren die Dateien unter quellcodeverwaltung ermöglicht  
  
-   Verwalten des Prozesses, durch den die Überwachung von Elementen von einer Person auf eine andere übertragen wird. Quellcodeverwaltungsanbieter unterstützen den gemeinsamen und den exklusiven Zugriff auf Dateien. Beim exklusiven Zugriff auf Projektdateien ermöglicht es der Quellcodeverwaltungsanbieter nur jeweils einem Benutzer, Dateien auszuchecken und zu ändern. Beim gemeinsamen Zugriff kann mehr als ein Benutzer die Skriptdatei auschecken, und der Quellcodeverwaltungsanbieter verfügt über einen Mechanismus zur Versionszusammenführung beim Einchecken.  
  
-   Archivieren von Folgeversionen quellcodeverwalteter Elemente. Ein Quellcodeverwaltungsanbieter speichert die Daten, mit denen die Versionen quellcodeverwalteter Elemente voneinander unterschieden werden. Der Anbieter speichert die Unterschiede zwischen Versionen und wichtige Versionsinformationen, z. B. wann und von wem die Version erstellt oder geändert wurde. Wenn mehrere Leute an derselben Datei arbeiten, müssen sie dieselbe Codepage verwenden, damit die Versionen präzise miteinander verglichen werden können. Sie können also eine beliebige Version eines quellcodeverwalteten Elements abrufen. Sie können außerdem eine beliebige Version als aktuelle Version des Elements festlegen.  
  
-   Verwalten von detaillierten Verlaufs- und Versionsinformationen zu quellcodeverwalteten Elementen. Die Quellcodeverwaltung speichert Datum und Uhrzeit für die Erstellung, das Einchecken und das Auschecken des Elements sowie den Benutzer, der den Vorgang ausgeführt hat.  
  
-   Projektübergreifendes Zusammenarbeiten. Durch die Freigabe von Dateien können quellcodeverwaltete Elemente in mehreren Projekten verwendet werden. Änderungen an einem freigegebenen Element spiegeln sich in allen Projekten wider, in denen das Element gemeinsam verwendet wird.  
  
-   Automatisieren regelmäßig ausgeführter Quellcodeverwaltungsvorgänge. Ein Quellcodeverwaltungsanbieter kann eine Schnittstelle von der Eingabeaufforderung definieren, die die Schlüsselfunktionen der Quellcodeverwaltung unterstützt. Mit dieser Schnittstelle können Sie in Batchdateien die Quellcodeverwaltungsaufgaben automatisieren, die Sie regelmäßig ausführen.  
  
-   Wiederherstellen von versehentlich gelöschten Dateien. Sie können die Dateiversion wiederherstellen, die zuletzt in die Quellcodeverwaltung eingecheckt wurde.  
  
-   Einsparen von Speicherplatz auf dem Client der Quellcodeverwaltung und auf dem Server. Bei einigen Quellcodeverwaltungsanbietern, z. B. [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, wird die Einsparung von Speicherplatz dadurch erzielt, dass die letzte Version einer Datei und die Unterschiede zwischen den einzelnen aufeinander folgenden Versionen gespeichert werden. Auf dem Client unterstützt Visual SourceSafe die Einsparung von Speicherplatz. Sie können Ordner und Dateien verdecken, damit sie nicht auf den lokalen Datenträger heruntergeladen werden.  
  
 Das Auschecken und Einchecken von Dateien und andere Quellcodeverwaltungsvorgänge werden von einem Quellcodeverwaltungsclient vorgenommen, z. B. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Der Client wurde so entworfen, dass er mit dem Anbieter interagiert, um einer verteilten Benutzergruppe die Fähigkeiten des Anbieters zur Verfügung zu stellen. Mit einem Quellcodeverwaltungsclient können Benutzer die Dateien durchsuchen, die vom Anbieter gespeichert wurden, Dateien hinzufügen und löschen, Dateien ein- und auschecken sowie Kopien lokaler Dateien abrufen.  
  
> [!NOTE]  
>  In dieser Dokumentation wird davon ausgegangen, dass Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe als Quellcodeverwaltungsanbieter verwenden. Wenn Sie einen anderen Quellcodeverwaltungsanbieter verwenden, weichen die Beschreibungen in dieser Dokumentation möglicherweise in einigen Punkten von der ausgeführten Software ab. Wenn Sie Unterschiede feststellen, schlagen Sie in der entsprechenden Dokumentation des Quellcodeverwaltungsanbieters nach.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Task**|**Thema**|  
|Festlegen von Optionen des Datenquellen-Steuerelement|[Festlegen von Quellcodeverwaltungsoptionen](../../2014/database-engine/set-source-control-options.md)|  
|Ändern Sie die quellcodeverwaltung Verbindungen|[Ändern von Quellcodeverwaltungsverbindungen](../../2014/database-engine/change-source-control-connections.md)|  
|Ausschließen von Dateien aus der quellcodeverwaltung|[Ausschließen von Dateien aus der Quellcodeverwaltung](../../2014/database-engine/exclude-files-from-source-control.md)|  
  
  
