---
description: Typen von Sperren
title: Arten von Sperren | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 55087e96c0855f24153dee9bc279d9abf58d3f04
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979261"
---
# <a name="types-of-locks"></a>Typen von Sperren
## <a name="adlockbatchoptimistic"></a>adlockbatchoptimistische  
 Gibt Updates für optimistische Batches an. Erforderlich für den Batch Aktualisierungs Modus.  
  
 Viele Anwendungen rufen eine Reihe von Zeilen gleichzeitig ab und müssen dann koordinierte Updates erstellen, die den gesamten Satz von Zeilen enthalten, die eingefügt, aktualisiert oder gelöscht werden sollen. Bei Batch Cursorn ist nur ein Roundtrip zum Server erforderlich, um die Update Leistung zu verbessern und den Netzwerk Datenverkehr zu verringern. Mithilfe einer Batch Cursor Bibliothek können Sie einen statischen Cursor erstellen und dann die Verbindung mit der Datenquelle trennen. An diesem Punkt können Sie Änderungen an den Zeilen vornehmen und anschließend erneut eine Verbindung herstellen und die Änderungen an der Datenquelle in einem Batch veröffentlichen.  
  
## <a name="adlockoptimistic"></a>adlockoptimistisch  
 Gibt an, dass der Anbieter nur dann Datensätze mit optimistischer sperrsperre verwendet, wenn Sie die **Update** -Methode aufruft. Dies bedeutet, dass es möglich ist, dass ein anderer Benutzer die Daten zwischen dem Zeitpunkt, zu dem Sie den Datensatz bearbeiten, und dem Aufruf von **Update**, der Konflikte erstellt, ändern kann. Verwenden Sie diesen Sperrentyp in Situationen, in denen die Wahrscheinlichkeit einer Kollision gering ist oder Konflikte problemlos gelöst werden können.  
  
## <a name="adlockpessimistic"></a>adlockpessimi  
 Gibt eine pessimistische Sperrung an, Daten Satz nach Datensatz. Der Anbieter übernimmt das, was erforderlich ist, um eine erfolgreiche Bearbeitung der Datensätze sicherzustellen, normalerweise durch Sperren von Datensätzen in der Datenquelle unmittelbar vor der Bearbeitung. Dies bedeutet natürlich, dass die Datensätze für andere Benutzer nicht verfügbar sind, wenn Sie mit der Bearbeitung beginnen, bis Sie die Sperre durch Aufrufen von **Update freigeben.** Verwenden Sie diese Art von Sperre in einem System, in dem Sie keine gleichzeitigen Änderungen an Daten, z. b. in einem Reservierungssystem, vornehmen können.  
  
## <a name="adlockreadonly"></a>adlockread Only  
 Gibt schreibgeschützte Datensätze an. Sie können die Daten nicht ändern. Eine schreibgeschützte Sperre ist der "schnellste" Sperrentyp, da der Server keine Sperre für die Datensätze benötigt.  
  
## <a name="adlockunspecified"></a>adlockunspezifiziert  
 Gibt keinen Sperrentyp an.
