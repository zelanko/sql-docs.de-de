---
title: Eigenschaften für die SQL Server-Browser (Registerkarte Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98b3cbf3089d1c10ffaf63072c2b488a4559b45e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222260"
---
# <a name="sql-server-browser-properties-service-tab"></a>Eigenschaften von SQL Server-Browser (Registerkarte Dienst)
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Programm wird als Dienst auf dem Server ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser lauscht auf eingehende Anforderungen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen und stellt Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen zur Verfügung, die auf dem Computer installiert sind.  
  
 Verwenden Sie im Dialogfeld **Eigenschaften von SQL Server-Browser** die Registerkarte **Dienst** , um die folgenden Optionen anzuzeigen. Alle Eigenschaften außer **Startmodus** sind schreibgeschützt.  
  
## <a name="options"></a>Tastatur  
 **Binärpfad**  
 Zeigt den Speicherort der Programmdateien an, die von diesem Dienst verwendet werden.  
  
 **Fehlersteuerung**  
 1 steht für `SERVICE_ERROR_NORMAL`. Wenn der Dienst nicht zusammen mit dem Computer gestartet werden kann, wird der Fehler vom Startprogramm protokolliert und eine Popupmeldung angezeigt, der Startvorgang aber fortgesetzt. Dieser Wert kann nicht geändert werden.  
  
 **Exitcode**  
 Bei einem Fehler wird die dazu gehörende Nummer in diesem Feld angezeigt. Verwenden Sie diese Nummer für die Problembehandlung. Stellen Sie die Fehlernummer dem technischen Support zur Verfügung, oder durchsuchen Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.  
  
 **HostName**  
 Zeigt den Namen des Computers oder Clusters an, auf dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst ausgeführt wird.  
  
 **Name**  
 Zeigt den Anzeigenamen des Dienstes an.  
  
 **Prozess-ID**  
 Zeigt die Prozess-ID von Windows an.  
  
 **Diensttyp**  
 Zeigt den für aufrufende Prozesse bereitgestellten Diensttyp an. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mehrere Dienste installiert.  
  
 **Startmodus**  
 Richten Sie den Dienst mit den folgenden Auswahlmöglichkeiten ein:  
  
-   Manuell: Dieser Dienst wird nicht automatisch zusammen mit dem Computer gestartet. Zum Starten des Dienstes verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder ein anderes Tool.  
  
-   Automatisch: Dieser Dienst wird zusammen mit dem Computer gestartet.  
  
-   Deaktiviert: Dieser Dienst kann nicht gestartet werden.  
  
 **Status**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist. "**…**" gibt einen ausstehenden Statuswechsel an.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Browserdienst](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
