---
title: Cursor und Merkmale der Sperre | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a3a206a21cf7c6680a656c89c48b8f52d1069d78
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702115"
---
# <a name="cursor-and-lock-characteristics"></a>Cursor und Merkmale der Sperre
Während die Merkmale eines Cursors auf Funktionen des Anbieters abhängig sind, gelten sich die folgenden vor- und Nachteile in der Regel für die verschiedenen Typen von Cursors und sperren.  
  
|Cursor oder Lock-Typ|Vorteile|Nachteile|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|– Anforderungen niedrig|-Kann nicht rückwärts scrollen<br />– Keine Datenparallelität|  
|**adOpenStatic**|-Bildlauffähigen|– Keine Datenparallelität|  
|**adOpenKeyset**|– Einige Datenparallelität<br />-Bildlauffähigen|-Höhere Anforderungen an die Ressource<br />-Nicht verfügbar in nicht verbundenen Szenario|  
|**adOpenDynamic**|– Hohe Parallelität<br />-Bildlauffähigen|-Höchste ressourcenanforderungen<br />-Nicht verfügbar in nicht verbundenen Szenario|  
|**adLockReadOnly**|– Anforderungen niedrig<br />-Hochgradig skalierbaren|-Daten durch Cursor nicht aktualisiert.|  
|**adLockBatchOptimistic**|-Batch updates<br />– Ermöglicht das unverbundenen Szenarien<br />-Andere Benutzer, die auf Daten zugreifen können|-Daten können von mehreren Benutzern gleichzeitig geändert werden|  
|**adLockPessimistic**|-Daten können nicht geändert werden, von anderen Benutzern, die gesperrten Modus|– Verhindert, dass anderen Benutzern den Zugriff auf Daten während Sperrung|  
|**adLockOptimistic**|-Andere Benutzer, die auf Daten zugreifen können|-Daten können von mehreren Benutzern gleichzeitig geändert werden|
