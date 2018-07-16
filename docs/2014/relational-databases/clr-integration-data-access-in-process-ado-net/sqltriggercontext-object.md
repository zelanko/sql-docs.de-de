---
title: SqlTriggerContext-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ff176908a3ef66f9c1d14d1c5a695932075e8735
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353272"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext-Objekt
  Die `SqlTriggerContext` -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, die bei einem UPDATE-Vorgang aktualisierten Spalten und im Falle eines DDL-Triggers (Data Definition Language) eine XML-`EventData`-Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen und Beispiele zur Verwendung der `SqlTriggerContext` Klasse, finden Sie unter [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md).  
  
 Weitere Informationen finden Sie unter den `Microsoft.SqlServer.Server.SqlTriggerContext` Klasse Referenzdokumentation finden Sie in der .NET Framework SDK-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
