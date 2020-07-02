---
title: SqlTriggerContext-Objekt | Microsoft-Dokumentation
description: In SQL Server CLR-Integration stellt die SqlTriggerContext-Klasse Kontextinformationen für einen Trigger bereit, einschließlich der Art der Aktion und der Spalten, die im Vorgang geändert wurden.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
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
ms.openlocfilehash: 4634a0c95e64516b6364fbfd68edeb9cd6156511
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765408"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die **SqlTriggerContext** -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, die bei einem UPDATE-Vorgang aktualisierten Spalten und im Falle eines DDL-Triggers (Data Definition Language) eine XML- **EventData** -Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen und Beispiele zur Verwendung der **SqlTriggerContext** -Klasse finden Sie unter [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Weitere Informationen finden Sie in der Dokumentation zur **Microsoft. SqlServer. Server. SqlTriggerContext** -Klasse in der .NET Framework SDK-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
