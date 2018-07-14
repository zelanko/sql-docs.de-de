---
title: Verbindungsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
caps.latest.revision: 30
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba6652a172e06c64018243acd01a6d60dcced47b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181617"
---
# <a name="connection-parameters"></a>Verbindungsparameter
  Um bestimmte Servertypen, z. B. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], zu analysieren, müssen Sie eine bestimmte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswählen. Die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird automatisch ausgewählt. Sie können diese Auswahl ändern, aber Sie können jeweils nur eine Instanz für die Analyse durch den Upgrade Advisor auswählen. Wenn Sie einen Servertyp aufgenommen haben, der eine Authentifizierung erfordert, müssen Sie den Authentifizierungsmodus und die Anmeldeinformationen eingeben.  
  
## <a name="options"></a>Tastatur  
 **Servername**  
 Ist mit dem Computernamen vorab aufgefüllt, den Sie im Bereich mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten eingegeben haben.  
  
 **Instanzname**  
 Wählen Sie eine Instanz aus den Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus, die auf dem Computer verfügbar sind. Wenn Sie eine Liste der Instanzen nicht angezeigt werden, verwenden Sie MSSQLSERVER auf um der Standardinstanz zu scannen. Dies ist für Remotecomputer besonders wichtig. Sie können auch das Wort "default" verwenden, um die Standardinstanz zu scannen.  
  
 **Authentifizierung**  
 Wählen Sie auf diesem Computer einen Eintrag aus der Liste der verfügbaren Authentifizierungsmodi aus. Die Windows-Authentifizierung ist der Standardauthentifizierungsmodus.  
  
 **Benutzername**  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden, geben Sie einen Benutzernamen in das Feld ein. Es wird empfohlen, einen Benutzernamen einzugeben, der auf dem Computer Administratorrechte hat.  
  
> [!NOTE]  
>  Wenn Sie Windows-Authentifizierung auswählen, wird in der Benutzernamen des aktuell angemeldeten Benutzers aufgefüllt der **Benutzernamen** Textfeld.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den angegebenen Benutzer ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Upgrade Advisor Referenz zur Benutzeroberfläche](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
