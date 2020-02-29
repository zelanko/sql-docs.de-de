---
title: Option „status“ (Verwaltungstool Distributed Replay) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e56a5229f0f26dfe701a425653b3d7f5a4ece842
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171939"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Option Status (Verwaltungstool Distributed Replay)
  Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Verwaltungs Tool, `DReplay.exe`, ist ein Befehlszeilen Tool, das Sie für die Kommunikation mit dem verteilten Replay-Controller verwenden können. In diesem Thema werden die Befehlszeilenoption **status** und die entsprechende Syntax beschrieben.

 Mit der **status** -Option wird der Controller abgefragt und der aktuelle Status angezeigt.

 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Symbol für Themenlink") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Syntax

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a>Parameter
 **-m** *Controller* gibt den Computernamen des Controllers an. Sie können mit "`localhost`" oder "`.`" auf den lokalen Computer verweisen.

 Wenn der **-m** -Parameter nicht angegeben ist, wird der lokale Computer verwendet.

 **-f** *status_interval* gibt die Häufigkeit (in Sekunden) an, mit der der Status angezeigt wird.

 Wenn der **-f** -Parameter nicht angegeben wird, ist das Standardintervall 30 Sekunden.

## <a name="examples"></a>Beispiele
 Im folgenden Beispiel wird der aktuelle Status alle 60 Sekunden angezeigt. Der Wert `localhost` gibt an, dass der Controllerdienst auf demselben Computer wie das Verwaltungstool ausgeführt wird.

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a>Berechtigungen
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.

 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Weitere Informationen
 [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)


