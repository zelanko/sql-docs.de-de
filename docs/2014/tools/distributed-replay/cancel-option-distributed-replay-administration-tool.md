---
title: Option „cancel“ (Verwaltungstool Distributed Replay) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6d9aa28d4a6879f3077b137880aae54b9a0c434
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822284"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Option Abbrechen (Verwaltungstool Distributed Replay)
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Verwaltungstool, `DReplay.exe`, ist ein Befehlszeilentool, das Sie für die Kommunikation mit distributed Replay Controller verwenden können. In diesem Thema werden die **cancel** -Befehlszeilenoption und die entsprechende Syntax beschrieben.  
  
 Die **cancel** -Option bricht den aktuellen Vorgang ab, der auf dem Controller ausgeführt wird.  
  
 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Topic link icon") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dreplay cancel [-mcontroller] [-q]   
```  
  
#### <a name="parameters"></a>Parameter  
 **-m** *controller*  
 Der Computername des Controllers. Sie können mit "`localhost`" oder "`.`" auf den lokalen Computer verweisen.  
  
 Wenn der **-m** -Parameter nicht angegeben ist, wird der lokale Computer verwendet.  
  
 **-q**  
 Stiller Modus. Fordert nicht zur Bestätigung auf.  
  
 Der **-q** -Parameter ist optional.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Abbruchanforderung im stillen Modus gesendet. Der Wert `localhost` gibt an, dass der Controllerdienst auf demselben Computer wie das Verwaltungstool ausgeführt wird.  
  
```  
dreplay cancel -m localhost -q  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
