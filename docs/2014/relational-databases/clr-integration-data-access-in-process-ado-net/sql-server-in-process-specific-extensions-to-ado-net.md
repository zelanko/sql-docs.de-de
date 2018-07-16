---
title: SQL Server In-Process-spezifische Erweiterungen für ADO.NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bd625f2b09f70e7356c169248953786c70dd1ad9
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354942"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET
  Es gibt vier Hauptfunktionserweiterungen für ADO.NET, die speziell der prozessinternen Verwendung dienen. Die folgenden Themen liefern detaillierte Informationen zu diesen Erweiterungen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [SqlContext-Objekt](sqlcontext-object.md)  
 Diese Klasse bietet Zugriff auf die anderen Erweiterungen, indem sie den Kontext des Aufrufers einer SQL Server-Routine abstrahiert, die verwalteten Code prozessintern ausführt.  
  
 [SqlPipe-Objekt](sqlpipe-object.md)  
 Diese Klasse enthält Routinen, mit denen Tabellenergebnisse und Nachrichten an den Client gesendet werden.  
  
 [SqlTriggerContext-Objekt](sqltriggercontext-object.md)  
 Diese Klasse stellt Informationen über den Kontext bereit, in dem ein Trigger ausgeführt wird.  
  
 [SqlDataRecord-Objekt](sqldatarecord-object.md)  
 Die SqlDataRecord-Klasse stellt eine einzelne Datenzeile einschließlich der zugehörigen Metadaten dar und ermöglicht es gespeicherten Prozeduren, benutzerdefinierte Resultsets an den Client zurückzugeben.  
  
  
