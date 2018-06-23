---
title: Links in Sicherheit der CLR-Integration | Microsoft Docs
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
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: edd8600e3c8e577ef020d732cce3924252393ce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162089"
---
# <a name="links-in-clr-integration-security"></a>Links in Sicherheit der CLR-Integration
  In diesem Abschnitt wird beschrieben, wie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Teile des Benutzercodes andere Benutzercodeteile in [!INCLUDE[tsql](../../includes/tsql-md.md)] oder einer der verwalteten Sprachen aufrufen können. Diese Beziehungen zwischen Objekten werden als Links bezeichnet.  
  
## <a name="invocation-links"></a>Aufruflinks  
 Aufruflinks entsprechen einem Codeaufruf, entweder von einem Benutzer, der Aufruf eines Objekts (z. B. eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch Aufrufen einer gespeicherten Prozedur), oder eine common Language Runtime (CLR) gespeicherte Prozedur oder Funktion. Aufruflinks bewirken eine Überprüfung der `EXECUTE`-Berechtigung für den aufgerufenen Code.  
  
## <a name="table-access-links"></a>Tabellenzugriffslinks  
 Tabellenzugriffslinks entsprechen dem Abrufen oder Ändern von Werten in einer Tabelle, Sicht oder Tabellenwertfunktion. Sie gleichen Aufruflinks, verfügen jedoch durch die SELECT-, INSERT-, UPDATE- und DELETE-Berechtigungen über eine differenziertere Zugriffssteuerung.  
  
## <a name="gated-links"></a>Gated Links  
 Gated Links bedeuten, dass die Berechtigungen für eine Objektbeziehung während der Ausführung nicht mehr überprüft werden, sobald die Beziehung hergestellt wurde. Wenn zwischen zwei Objekten (beispielsweise Objekt **x** und Objekt **y**) ein Gated Link besteht, dann werden die Berechtigungen für Objekt **y** und andere Objekte, auf die von Objekt **y** aus zugegriffen wird, nur während der Erstellung von Objekt **x**überprüft. Bei der Erstellung des Objekts **x**, `REFERENCE` Berechtigung wird geprüft, ob **y** für den Besitzer des **x**. Während der Codeausführung (wenn beispielsweise das Objekt **x**aufgerufen wird) werden keine Berechtigungen für Objekt **y** oder andere Objekte überprüft, auf die dieses Objekt statisch verweist. Während der Ausführung wird überprüft, ob eine entsprechende Berechtigung für Objekt **x** selbst vorliegt.  
  
 Gated Links werden immer in Verbindung mit einer Metadatenabhängigkeit zwischen zwei Objekten verwendet. Diese Metadatenabhängigkeit ist eine Beziehung, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Katalogen eingerichtet wird und verhindert, dass ein Objekt solange nicht freigegeben wird, solange ein anderes Objekt von ihm abhängt.  
  
 Gated Links sind nützlich, wenn es nicht angemessen oder praktikabel ist, vielen abhängigen Objekten Berechtigungen zu erteilen. Gated Links zwischen Objekten, die definieren eingeführt [!INCLUDE[tsql](../../includes/tsql-md.md)] -Einstiegspunkte in CLR-Assemblys (z. B. CLR Prozeduren, Trigger, Funktionen, Typen und Aggregate) und die Assemblys, von dem sie definiert sind. Der Schutz dieser Objekte durch Gated Links hat zur Folge, dass ein in einer CLR-Assembly definierter [!INCLUDE[tsql](../../includes/tsql-md.md)]-Einstiegspunkt aufgerufen werden kann, wenn der Aufrufer über die entsprechende Berechtigung für diesen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Eintrittspunkt verfügt. Der Aufrufer muss nicht über Berechtigungen für die Assembly oder andere Assemblys, auf die diese statisch verweist, verfügen. Die Berechtigungen für die Assembly werden zur Erstellungszeit des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Einstiegspunkts überprüft.  
  
## <a name="sql-server-authorization-based-security"></a>Auf der SQL Server-Autorisierung basierende Sicherheit  
 Im folgenden sind die grundlegenden Regeln hinter der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -sicherheitsprüfungen von Aufrufen von und zwischen CLR-basierten Datenbankobjekten; die ersten drei Regeln definieren, welche Berechtigungen überprüft werden, und für welches Objekt; die vierte Regel definiert, die die Ausführung Kontext die Berechtigung überprüft wird.  
  
1.  Alle Aufrufe erfordern `EXECUTE` Berechtigung, sofern die Aufrufe nicht innerhalb desselben Objekts erfolgen Dies bedeutet, dass Aufrufe innerhalb der gleichen Assembly keine Berechtigungen überprüft erforderlich sind. Die Berechtigung wird während der Ausführung überprüft.  
  
2.  Bei Gated Links ist eine `REFERENCE`-Berechtigung für das aufgerufene Objekt erforderlich, wenn das aufrufende Objekt erstellt wird. Bei der Objekterstellung wird geprüft, ob der Besitzer des aufrufenden Objekts über diese Berechtigung verfügt.  
  
3.  Tabellenzugriffslinks erfordern das entsprechende `SELECT`, `INSERT`, `UPDATE`, oder `DELETE` Berechtigung für eine Tabelle oder Sicht zugegriffen wird.  
  
4.  Die Berechtigung wird im aktuellen Ausführungskontext überprüft. Prozeduren und Funktionen können mit einem Ausführungskontext erstellt werden, der sich vom Aufrufer unterscheidet. Assemblys werden immer mit dem Ausführungskontexts der Prozedur, der Funktion oder des Triggers erstellt, die bzw. der für sie definiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  