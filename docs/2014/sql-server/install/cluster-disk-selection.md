---
title: Datenträgerauswahl für Cluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea021ed6e3613d4a39641c582e0b091ebfe1a6f1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52519663"
---
# <a name="cluster-disk-selection"></a>Datenträgerauswahl für Cluster
  Verwenden Sie die Seite **Datenträgerauswahl für Cluster** des Installations-Assistenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die freigegebene Cluster-Datenträgerressource für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster auszuwählen. Auf dem Clusterdatenträger werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten platziert.  
  
 Ein freigegebener Clusterdatenträger ist keine Voraussetzung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] failoverclusterinstallationen. Ein SMB-Dateiserver ist ein unterstützter Speicher für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] Failover failoverclusterinstallationen und kann angegeben werden, mithilfe der **Datenbank-Engine – Datenverzeichnisse** Seite vor dem Abschluss der Installation.  
  
> [!WARNING]  
>  Wenn Sie Analysis Services installieren möchten, müssen Sie einen freigegebenen Clusterdatenträger angeben.  
>   
>  Wenn FILESTREAM in dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz aktiviert werden soll, müssen Sie einen freigegebenen Clusterdatenträger angeben.  
  
## <a name="options"></a>Optionen  
 **Freigegebene Datenträger**  
 Wählen Sie einen Datenträger aus der Liste aus. Auf dem Clusterdatenträger werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten platziert.  
  
 Es kann nur ein Datenträger angegeben werden. Wenn Sie die Gruppe mit der Quorumressource des Clusters auswählen, wird eine Warnung angezeigt. Von einer Installation in der Quorumressource des Clusters wird abgeraten.  
  
 **Verfügbare freigegebene Datenträger**  
 Zeigt eine Liste der verfügbaren Datenträger, Informationen zur Qualifikation der Datenträger als freigegebene Datenträger und eine Beschreibung der einzelnen Datenträgerressourcen an.  
  
  
