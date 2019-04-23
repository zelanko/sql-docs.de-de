---
title: Links im CLR-Integrationssicherheit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37aa64129658128bd7297f147f317166917e05a6
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156776"
---
# <a name="links-in-clr-integration-security"></a>Links in Sicherheit der CLR-Integration
  In diesem Abschnitt wird beschrieben, wie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Teile des Benutzercodes andere Benutzercodeteile in [!INCLUDE[tsql](../../includes/tsql-md.md)] oder einer der verwalteten Sprachen aufrufen können. Diese Beziehungen zwischen Objekten werden als Links bezeichnet.  
  
## <a name="invocation-links"></a>Aufruflinks  
 Aufruflinks entsprechen einem Codeaufruf, beispielsweise wenn ein Benutzer ein Objekt (z. B. der Aufruf einer gespeicherten Prozedur durch einen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batch) oder eine gespeicherte CLR-Prozedur (Common Language Runtime) oder Funktion aufruft. Aufruflinks bewirken eine Überprüfung der `EXECUTE`-Berechtigung für den aufgerufenen Code.  
  
## <a name="table-access-links"></a>Tabellenzugriffslinks  
 Tabellenzugriffslinks entsprechen dem Abrufen oder Ändern von Werten in einer Tabelle, Sicht oder Tabellenwertfunktion. Sie gleichen Aufruflinks, verfügen jedoch durch die SELECT-, INSERT-, UPDATE- und DELETE-Berechtigungen über eine differenziertere Zugriffssteuerung.  
  
## <a name="gated-links"></a>Gated Links  
 Gated Links bedeuten, dass die Berechtigungen für eine Objektbeziehung während der Ausführung nicht mehr überprüft werden, sobald die Beziehung hergestellt wurde. Wenn zwischen zwei Objekten (beispielsweise Objekt **x** und Objekt **y**) ein Gated Link besteht, dann werden die Berechtigungen für Objekt **y** und andere Objekte, auf die von Objekt **y** aus zugegriffen wird, nur während der Erstellung von Objekt **x**überprüft. Bei der Erstellung des Objekts **x**, `REFERENCE` Berechtigung wird geprüft, ob **y** für den Besitzer des **x**. Während der Codeausführung (wenn beispielsweise das Objekt **x**aufgerufen wird) werden keine Berechtigungen für Objekt **y** oder andere Objekte überprüft, auf die dieses Objekt statisch verweist. Während der Ausführung wird überprüft, ob eine entsprechende Berechtigung für Objekt **x** selbst vorliegt.  
  
 Gated Links werden immer in Verbindung mit einer Metadatenabhängigkeit zwischen zwei Objekten verwendet. Diese Metadatenabhängigkeit ist eine Beziehung, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Katalogen eingerichtet wird und verhindert, dass ein Objekt solange nicht freigegeben wird, solange ein anderes Objekt von ihm abhängt.  
  
 Gated Links sind nützlich, wenn es nicht angemessen oder praktikabel ist, vielen abhängigen Objekten Berechtigungen zu erteilen. Gated Links werden zwischen Objekten eingeführt, die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Einstiegspunkte in CLR-Assemblys (z. B. CLR-Prozeduren, Trigger, Funktionen, Typen und Aggregate) und die Assemblys definieren, von denen diese definiert werden. Der Schutz dieser Objekte durch Gated Links hat zur Folge, dass ein in einer CLR-Assembly definierter [!INCLUDE[tsql](../../includes/tsql-md.md)] -Einstiegspunkt aufgerufen werden kann, wenn der Aufrufer über die entsprechende Berechtigung für diesen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Eintrittspunkt verfügt. Der Aufrufer muss nicht über Berechtigungen für die Assembly oder andere Assemblys, auf die diese statisch verweist, verfügen. Die Berechtigungen für die Assembly werden zur Erstellungszeit des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Einstiegspunkts überprüft.  
  
## <a name="sql-server-authorization-based-security"></a>Auf der SQL Server-Autorisierung basierende Sicherheit  
 Im Folgenden werden die Grundregeln beschrieben, die den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsprüfungen von Aufrufen von und zwischen CLR-basierten Datenobjekten zugrunde liegen. Die ersten drei Regeln definieren, welche Berechtigungen für welches Objekt überprüft werden. Die vierte Regel definiert, für welchen Ausführungskontext die Berechtigung überprüft wird.  
  
1.  Sofern die Aufrufe nicht innerhalb desselben Objekts erfolgen, ist für alle Aufrufe die `EXECUTE`-Berechtigung erforderlich. Das bedeutet, dass für Aufrufe innerhalb einer Assembly keine Berechtigungen überprüft werden müssen. Die Berechtigung wird während der Ausführung überprüft.  
  
2.  Bei Gated Links ist eine `REFERENCE`-Berechtigung für das aufgerufene Objekt erforderlich, wenn das aufrufende Objekt erstellt wird. Bei der Objekterstellung wird geprüft, ob der Besitzer des aufrufenden Objekts über diese Berechtigung verfügt.  
  
3.  Tabellenzugriffslinks erfordern beim Zugriff auf die Tabelle oder Sicht die entsprechende `SELECT`, `INSERT`-, `UPDATE`- bzw. `DELETE`-Berechtigung.  
  
4.  Die Berechtigung wird im aktuellen Ausführungskontext überprüft. Prozeduren und Funktionen können mit einem Ausführungskontext erstellt werden, der sich vom Aufrufer unterscheidet. Assemblys werden immer mit dem Ausführungskontexts der Prozedur, der Funktion oder des Triggers erstellt, die bzw. der für sie definiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
