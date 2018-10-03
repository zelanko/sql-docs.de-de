---
title: SqlTriggerContext-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: df384324ba16aac03a4c889cf4f3959c23374510
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158670"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext-Objekt
  Die `SqlTriggerContext` -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, die bei einem UPDATE-Vorgang aktualisierten Spalten und im Falle eines DDL-Triggers (Data Definition Language) eine XML-`EventData`-Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen und Beispiele zur Verwendung der `SqlTriggerContext` Klasse, finden Sie unter [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md).  
  
 Weitere Informationen finden Sie unter den `Microsoft.SqlServer.Server.SqlTriggerContext` Klasse Referenzdokumentation finden Sie in der .NET Framework SDK-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
