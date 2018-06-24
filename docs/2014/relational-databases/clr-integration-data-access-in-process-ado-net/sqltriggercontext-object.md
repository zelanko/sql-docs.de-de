---
title: SqlTriggerContext-Objekt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dbdaefa1e3c5e1c5a53cd6179f4b96320434dbdf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048269"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext-Objekt
  Die `SqlTriggerContext` -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, die bei einem UPDATE-Vorgang aktualisierten Spalten und im Falle eines DDL-Triggers (Data Definition Language) eine XML-`EventData`-Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen und Beispiele zum Verwenden der `SqlTriggerContext` Klasse, finden Sie unter [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md).  
  
 Weitere Informationen finden Sie unter der `Microsoft.SqlServer.Server.SqlTriggerContext` -Klasse Referenzdokumentation finden Sie in der .NET Framework SDK-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
