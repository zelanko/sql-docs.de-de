---
title: Ändern von Quellcodeverwaltungsverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cacfeef1468a0aec47ecd8e0b27a432bb689d1ef
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43812986"
---
# <a name="change-source-control-connections"></a>Ändern von Quellcodeverwaltungsverbindungen
  Wenn Sie zum ersten Mal eine Projektmappe aus der Quellcodeverwaltung öffnen oder hinzufügen, erstellt der Quellcodeverwaltungsanbieter eine Zuordnung zwischen dem Stammordner des lokalen Projektmappenverzeichnisses und dem zugehörigen Serverordner.  
  
 Der Stammordner (auch als einheitlicher Stamm bezeichnet) befindet sich auf dem Client. Dabei handelt es sich um den Ordner, unter dem sich alle Dateien befinden, auf die eine Projektmappe oder ein Projekt verweist. Um nach der letzten Version einer Projektmappe, deren Verlauf und deren Statusinformationen zu suchen, ermitteln Sie den Serverordner auf dem Quellcodeverwaltungsserver. In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe werden Serverordner als Projekte bezeichnet.  
  
 In vielen Situationen müssen Sie die Bindung oder Verbindung einer Projektmappe zum Serverordner aufheben. Wenn z. B. der Computer, auf dem sich der Quellcodeverwaltungsanbieter befindet, nicht verfügbar ist, können Sie eine Verbindung mit einem Sicherungscomputer herstellen, die Bindung der Projektmappe mit einem gesicherten Serverordner wieder herstellen und die Arbeit wie gewohnt fortsetzen. Oder wenn ein quellcodeverwaltetes Projekt verzweigt ist, müssen Sie möglicherweise eine Bindung zwischen der Projektmappe und dem Serverordner einrichten, in dem sich die neue Projektversion befindet.  
  
 Über die Benutzeroberfläche des Quellcodeverwaltungsanbieters können Sie den Serverordner ändern, zu dem die Bindung der Projektmappe besteht. Sie können die Benutzeroberfläche der Quellcodeverwaltung aus der [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Umgebung öffnen.  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>So öffnen Sie die Benutzeroberfläche der Quellcodeverwaltung aus der SQL Server Management Studio-Umgebung  
  
1.  Auf der **Datei** Startmenü **Quellcodeverwaltung**, und klicken Sie dann auf **starten Sie Microsoft Visual SourceSafe**.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen der Versionskontrolle](../../2014/database-engine/source-control-basics.md)   
 [Festlegen von Quellcodeverwaltungsoptionen](../../2014/database-engine/set-source-control-options.md)   
 [Ausschließen von Dateien aus der Quellcodeverwaltung](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
