---
title: Was ist eine Sperre? | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 59234b24d7a3e07c1d6500c41dd0ec2a16f95ee1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718378"
---
# <a name="what-is-a-lock"></a>Was ist eine Sperre?
Sperren ist der Prozess, der ein DBMS nach dem Zugriff auf eine Zeile in einer mehrbenutzerumgebung einschränkt. Wenn eine Zeile oder Spalte exklusiv gesperrt ist, sind andere Benutzer nicht zulässig, auf die gesperrten Daten zugreifen, bis die Sperre aufgehoben wird. Dadurch wird sichergestellt, dass zwei Benutzer gleichzeitig dieselbe Spalte in einer Zeile aktualisieren nicht möglich.  
  
 Sperren, können vom Standpunkt der Ressource sehr speicherintensiv sein und sollte nur bei Bedarf verwendet werden, um die Datenintegrität beizubehalten. In einer Datenbank, in denen Hunderte oder Tausende von Benutzern versuchen könnten, einen Datensatz pro Sekunde – z. B. eine Verbindung mit dem Internet - Datenbank zuzugreifen, kann das unnötige Sperren schnell zu Leistungseinbußen in Ihrer Anwendung führen.  
  
 Sie können steuern, wie die Datenquelle und die Cursorbibliothek ADO Parallelität zu verwalten die entsprechenden Sperre Option entscheiden.  
  
 Legen Sie die **LockType** Eigenschaft vor dem Öffnen einer **Recordset** angeben, welche Art von Sperre des Anbieters verwenden soll, beim Öffnen. Lesen die Eigenschaft, um den Typ der Sperre auf eine offene zurückzugeben **Recordset** Objekt.  
  
 Anbieter unterstützen möglicherweise nicht alle Typen von Sperren. Wenn ein Anbieter nicht die angeforderte unterstützt **LockType** festlegen, ersetzen sie einen anderen Typ von Sperren. Um zu bestimmen, die eigentliche Sperre Funktionalität, die in einem **Recordset** -Objekts die [unterstützt](../../../ado/reference/ado-api/supports-method.md) -Methode mit **AdUpdate** und **AdUpdateBatch**.  
  
 Die **AdLockPessimistic** Einstellung wird nicht unterstützt, wenn die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient.** Wenn Sie ein nicht unterstützter Wert festgelegt ist, wird kein Fehler gemeldet. die nächstgelegene unterstützt **LockType** wird stattdessen verwendet.  
  
 Die **LockType** -Eigenschaft ist Lese-/Schreibzugriff bei der **Recordset** ist geschlossen, und schreibgeschützt, wenn es geöffnet ist.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Typen von Sperren](../../../ado/guide/data/types-of-locks.md)
