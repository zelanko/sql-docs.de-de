---
title: SQL Server-Agent-Eigenschaften (Registerkarte „Anmelden“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b31cb3bc05f9785154b89033cde2e158f204b3c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779392"
---
# <a name="sql-server-agent-properties-log-on-tab"></a>SQL Server-Agent-Eigenschaften (Registerkarte Anmelden)
  Verwenden Sie im Dialogfeld **SQL Server-Agent-Eigenschaften** die Registerkarte **Anmelden** , um das vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentdienst verwendete Konto anzugeben und den Dienst zu starten und zu beenden. Das Ändern eines Kennworts für ein Konto wird sofort wirksam. Es ist kein Neustart des Dienstes erforderlich.  
  
> [!NOTE]  
>  Beim Ändern des Kontonamens, der von einem Dienst auf einer gruppierten Instanz verwendet wird, muss das neue Konto Mitglied der Domänengruppe sein, die während des Setups für den zu ändernden Dienst angegeben wird. Andernfalls müssen Sie die Berechtigung zum Hinzufügen von Mitgliedern zu dieser Gruppe besitzen. Wenden Sie sich an Ihren Domänenadministrator, falls Sie keine Berechtigung zum Ändern der Gruppenmitgliedschaft haben.  
  
## <a name="options"></a>Optionen  
 **Lokales System**  
 Geben Sie ein lokales Systemkonto an, das kein Kennwort erfordert. Das lokale Systemkonto kann sich allerdings einschränkend auf die Zusammenarbeit mit anderen Servern auswirken. Dies hängt von den Privilegien ab, die dem Konto erteilt wurden.  
  
 **Dieses Konto**  
 Geben Sie ein lokales oder ein Domänenbenutzerkonto an, das die Windows-Authentifizierung verwendet. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, ein Domänenbenutzerkonto mit minimalen Berechtigungen für Dienste zu verwenden. Informationen zum Auswählen eines Kontos finden Sie in der Onlinedokumentation unter "Einrichten von Windows-Dienstkonten".  
  
 **Kontoname**  
 Geben Sie den Kontonamen des lokalen oder Domänenbenutzers an.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Kontos ein.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort des Kontos erneut ein.  
  
 **Start**  
 Starten Sie den Dienst.  
  
 **Beenden**  
 Beenden Sie den Dienst.  
  
 **Anhalten**  
 Halten Sie den Dienst an.  
  
 **Fortsetzen**  
 Setzen Sie einen angehaltenen Dienst fort.  
  
  
