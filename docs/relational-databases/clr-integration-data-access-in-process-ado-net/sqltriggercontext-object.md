---
title: SqlTriggerContext-Objekt | Microsoft Docs
description: In der SQL Server CLR-Integration stellt die SqlTriggerContext-Klasse Kontextinformationen für einen Trigger bereit, einschließlich des Aktionstyps und der im Betrieb geänderten Spalten.
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
ms.openlocfilehash: 55e0ac850071615d9be7fb47442ed674eefab00a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487461"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die **SqlTriggerContext** -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, die bei einem UPDATE-Vorgang aktualisierten Spalten und im Falle eines DDL-Triggers (Data Definition Language) eine XML- **EventData** -Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen und Beispiele für die Verwendung der **SqlTriggerContext-Klasse** finden Sie unter [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Weitere Informationen finden Sie in der **Microsoft.SqlServer.Server.SqlTriggerContext-Klassenreferenzdokumentation** in der .NET Framework SDK-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
