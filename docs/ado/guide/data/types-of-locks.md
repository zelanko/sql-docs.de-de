---
title: Typen von Sperren | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AdLockBatchOptimistic [ADO]
- AdLockReadOnly [ADO]
- AdLockUnspecified [ADO]
- locks [ADO], types
- AdLockOptimistic [ADO]
- AdLockPessimistic [ADO]
ms.assetid: 12a978c0-b8a0-4ef0-87f0-a43c13659272
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 64ac7dae1a5760ff18f1a109a031bd00bb30eb1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718648"
---
# <a name="types-of-locks"></a>Typen von Sperren
## <a name="adlockbatchoptimistic"></a>adLockBatchOptimistic  
 Gibt die vollständige BatchUpdates an. Für den Modus "Batch-Update" erforderlich.  
  
 Viele Anwendungen eine Anzahl von Zeilen auf einmal abrufen und dann müssen Sie koordinierte Updates, die den gesamten Satz von Zeilen eingefügt, aktualisiert oder gelöscht werden, enthalten. Mit Batchcursorn, nur ein Roundtrip zum Server erforderlich ist, so die Leistung der Updates steigern und den Netzwerkverkehr zu verringern. Verwenden eine Batch-Cursorbibliothek, können Sie erstellen einen statischen Cursor und trennen Sie dann aus der Datenquelle. An diesem Punkt können Änderungen vornehmen, auf die Zeilen und nachfolgend erneut eine Verbindung herzustellen und die Änderungen bereitstellen, mit der Datenquelle in einem Batch.  
  
## <a name="adlockoptimistic"></a>adLockOptimistic  
 Gibt an, dass der Anbieter verwendet, optimistische Sperren: Sperren von Datensätzen nur bei Aufruf der **Update** Methode. Dies bedeutet, dass besteht die Möglichkeit, dass ein anderer Benutzer die Daten zwischen dem Zeitpunkt ändern, können Sie den Datensatz und beim Aufruf bearbeiten **Update**, wodurch Konflikte erstellt. Verwenden Sie diesen Sperren in Situationen, in denen die Wahrscheinlichkeit, dass ein Konflikt mit niedriger sind, oder, in denen Konflikte problemlos aufgelöst werden können.  
  
## <a name="adlockpessimistic"></a>adLockPessimistic  
 Gibt an, pessimistische Sperrung, Datensätze. Der Anbieter unterstützt, was erforderlich ist, um sicherzustellen, dass erfolgreiche Bearbeitung der Datensätze in der Regel durch Sperren von Datensätzen in der Datenquelle unmittelbar vor der Bearbeitung ist. Dies bedeutet natürlich, dass die Datensätze nicht an andere Benutzer verfügbar sind, sobald Sie beginnen, bis die Sperre durch den Aufruf zu bearbeiten, **aktualisieren.** Verwenden Sie diese Art von Sperre in einem System, in denen nicht Sie leisten um gleichzeitige Änderungen an Daten, z. B. in einem Reservierungssystem zu erhalten.  
  
## <a name="adlockreadonly"></a>adLockReadOnly  
 Gibt an, nur-Lese Datensätze. Sie können die Daten nicht ändern. Eine ReadOnly-Sperre ist der "Schnellstes" Typ der Sperre, da er nicht, dass der Server erfordert, um eine Sperre für die Datensätze zu verwalten.  
  
## <a name="adlockunspecified"></a>adLockUnspecified  
 Es gibt keine Art von Sperre.
