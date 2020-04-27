---
title: Verbindungsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca5d6ed8f1e8a92d22bd32e39c8afe946a0fcfee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095978"
---
# <a name="connection-parameters"></a>Verbindungsparameter
  Um bestimmte Servertypen, z. B. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], zu analysieren, müssen Sie eine bestimmte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswählen. Die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird automatisch ausgewählt. Sie können diese Auswahl ändern, aber Sie können jeweils nur eine Instanz für die Analyse durch den Upgrade Advisor auswählen. Wenn Sie einen Servertyp aufgenommen haben, der eine Authentifizierung erfordert, müssen Sie den Authentifizierungsmodus und die Anmeldeinformationen eingeben.  
  
## <a name="options"></a>Optionen  
 **Servername**  
 Ist mit dem Computernamen vorab aufgefüllt, den Sie im Bereich mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten eingegeben haben.  
  
 **Instanzname**  
 Wählen Sie eine Instanz aus den Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus, die auf dem Computer verfügbar sind. Wenn eine Liste von Instanzen nicht angezeigt wird, verwenden Sie MSSQLSERVER, um die Standard Instanz zu scannen. Dies ist für Remotecomputer besonders wichtig. Sie können auch das Wort "default" verwenden, um die Standardinstanz zu scannen.  
  
 **Authentifizierung**  
 Wählen Sie auf diesem Computer einen Eintrag aus der Liste der verfügbaren Authentifizierungsmodi aus. Die Windows-Authentifizierung ist der Standardauthentifizierungsmodus.  
  
 **Benutzername**  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden, geben Sie einen Benutzernamen in das Feld ein. Es wird empfohlen, einen Benutzernamen einzugeben, der auf dem Computer Administratorrechte hat.  
  
> [!NOTE]  
>  Wenn Sie die Windows-Authentifizierung auswählen, wird der Benutzername des aktuell angemeldeten Benutzers in das Textfeld **Benutzername** eingetragen.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den angegebenen Benutzer ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Benutzeroberflächenreferenz des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
