---
title: Eigenschaften von&lt;NS $&gt; -Dienst Name (Registerkarte "Dienst") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 57c6b791-1663-4a01-9de2-cf1bdd8adb2c
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 85cc46ae4f3d75493edc59f0376de625cebf4fdc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010030"
---
# <a name="nsltservice-namegt-properties-service-tab"></a>NS$&lt;Dienstname&gt;-Eigenschaften (Registerkarte „Dienst“)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Hierbei handelt es sich um den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNS](../../includes/ssns-md.md)] -Dienst. Die ausgegrauten Eigenschaftswerte können nicht mithilfe dieser Anwendung geändert werden.  
  
## <a name="options"></a>enthalten  
 **Binärpfad**  
 Zeigt den Speicherort der Programmdateien an, die von diesem Dienst verwendet werden.  
  
 **Fehlersteuerung**  
 1 steht für `SERVICE_ERROR_NORMAL`. Wenn der Dienst nicht zusammen mit dem Computer gestartet werden kann, wird der Fehler vom Startprogramm protokolliert und eine Popupmeldung angezeigt, der Startvorgang aber fortgesetzt. Dieser Wert kann nicht geändert werden.  
  
 **Exitcode**  
 Bei einem Fehler wird die dazu gehörende Nummer in diesem Feld angezeigt. Verwenden Sie diese Nummer für die Problembehandlung. Stellen Sie die Fehlernummer dem technischen Support zur Verfügung, oder durchsuchen Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.  
  
 **HostName**  
 Zeigt den Namen des Computers oder Clusters an, auf dem die Volltextsuche ausgeführt wird.  
  
 **Name**  
 Zeigt den Anzeigenamen des Dienstes an.  
  
 **Prozess-ID**  
 Zeigt die Prozess-ID von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows an.  
  
 **SQL-Diensttyp**  
 Der für aufrufende Prozesse bereitgestellte Diensttyp. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mehrere Dienste installiert.  
  
 **Startmodus**  
 Richten Sie den Dienst mit den folgenden Auswahlmöglichkeiten ein:  
  
-   Manuell: Dieser Dienst wird nicht automatisch zusammen mit dem Computer gestartet. Zum Starten des Dienstes verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder ein anderes Tool.  
  
-   Automatisch: Dieser Dienst wird zusammen mit dem Computer gestartet.  
  
-   Deaktiviert: Dieser Dienst kann nicht gestartet werden.  
  
 **Status**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist.  
  
  
