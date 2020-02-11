---
title: CDC Instance Deployment Script | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7b6665165d3b50ef4ac73be2d530a018c0ef5d86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62771566"
---
# <a name="cdc-instance-deployment-script"></a>CDC Instance Deployment Script
  In diesem Abschnitt wird das Dialogfeld CDC Instance Deployment Script beschrieben, in dem das Bereitstellungsskript der CDC-Instanz angezeigt wird. Dieses Skript kann verwendet werden, um die CDC-Datenbank mit ihren Artefakten auf einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz neu zu erstellen.  
  
 Nach Abschluss des Bereitstellungsskripts sollten Sie Folgendes sicherstellen:  
  
-   Das Bereitstellungsskript setzt voraus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz für Oracle CDC mit der Oracle CDC Service Configuration Console oder mit dem vom Programm erstellten **prepare script** (Vorbereitungsskript) vorbereitet wurde.  
  
-   Der Teil des Skripts, der zum Aktivieren der Datenbank für CDC verwendet wird, muss von einem `sysadmin`ausgeführt werden.  
  
-   Das Skript behält das Oracle Log Mining-Kennwort nicht bei. Das Kennwort muss manuell festgelegt werden, nachdem das Skript ausgeführt und der Oracle CDC Service gestartet wurde.  
  
 Aktivieren Sie im Dialogfeld **CDC Instance Deployment Script** die folgenden Optionen.  
  
 **Speichern unter**  
 Speichert das Skript in einer Textdatei, die Sie an einem beliebigen Speicherort ablegen können. Sie können die Datei mit dem Skript auf einen beliebigen anderen Server kopieren, um es dort auszuführen.  
  
 **Copy**  
 Kopiert das Skript in die Zwischenablage. Sie können das Skript dann in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder einen beliebigen Texteditor einfügen, um die Skripts später auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorbereiten von SQL Server für CDC](prepare-sql-server-for-cdc.md)  
  
  
