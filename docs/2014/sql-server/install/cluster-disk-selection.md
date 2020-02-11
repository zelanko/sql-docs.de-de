---
title: Cluster Datenträger Auswahl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 156c17d7dae5c4de07033a96f2e936448d8d02ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096497"
---
# <a name="cluster-disk-selection"></a>Datenträgerauswahl für Cluster
  Verwenden Sie die Seite **Datenträgerauswahl für Cluster** des Installations-Assistenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die freigegebene Cluster-Datenträgerressource für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster auszuwählen. Auf dem Clusterdatenträger werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten platziert.  
  
 Ein frei gegebener Cluster Datenträger ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] für Cluster Installationen nicht erforderlich. Ein SMB-Dateiserver ist ein unterstützter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] Speicher für-Failoverclusterinstallationen, der auf der Seite **Datenbank-Engine-Datenverzeichnisse** vor Abschluss der Installation angegeben werden kann.  
  
> [!WARNING]  
>  Wenn Sie Analysis Services installieren möchten, müssen Sie einen freigegebenen Clusterdatenträger angeben.  
>   
>  Wenn FILESTREAM in dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz aktiviert werden soll, müssen Sie einen freigegebenen Clusterdatenträger angeben.  
  
## <a name="options"></a>Tastatur  
 **Freigegebene Datenträger**  
 Wählen Sie einen Datenträger aus der Liste aus. Auf dem Clusterdatenträger werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten platziert.  
  
 Es kann nur ein Datenträger angegeben werden. Wenn Sie die Gruppe mit der Quorumressource des Clusters auswählen, wird eine Warnung angezeigt. Von einer Installation in der Quorumressource des Clusters wird abgeraten.  
  
 **Verfügbare freigegebene Datenträger**  
 Zeigt eine Liste der verfügbaren Datenträger, Informationen zur Qualifikation der Datenträger als freigegebene Datenträger und eine Beschreibung der einzelnen Datenträgerressourcen an.  
  
  
