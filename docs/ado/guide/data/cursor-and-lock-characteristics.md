---
description: Cursor und Merkmale der Sperre
title: Cursor-und Sperr Merkmale | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bd8b88ab3a90669982a752023d8a983c188dcbf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991461"
---
# <a name="cursor-and-lock-characteristics"></a>Cursor und Merkmale der Sperre
Obwohl die Merkmale eines Cursors von den Funktionen des Anbieters abhängen, gelten die folgenden vor-und Nachteile in der Regel für die verschiedenen Typen von Cursorn und sperren.  
  
|Cursor-oder Sperrentyp|Vorteile|Nachteile|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-Geringe Ressourcenanforderungen|-Kann nicht Rückwärtsscrollen<br />-Keine Daten Parallelität|  
|**adopkostatic**|-Scrollfähig|-Keine Daten Parallelität|  
|**adOpenKeyset**|-Einige Daten Parallelität<br />-Scrollfähig|-Höhere Ressourcenanforderungen<br />-Nicht in einem getrennten Szenario verfügbar|  
|**adOpenDynamic**|-Hohe Daten Parallelität<br />-Scrollfähig|-Höchste Ressourcenanforderungen<br />-Nicht in einem getrennten Szenario verfügbar|  
|**adlockread Only**|-Geringe Ressourcenanforderungen<br />-Hochgradig skalierbar|-Daten können nicht durch Cursor aktualisiert werden.|  
|**adlockbatchoptimistische**|-Batch Updates<br />-Ermöglicht getrennte Szenarios<br />-Andere Benutzer können auf Daten zugreifen.|-Daten können von mehreren Benutzern gleichzeitig geändert werden.|  
|**adlockpessimi**|-Daten können von anderen Benutzern nicht geändert werden, während Sie gesperrt sind.|-Verhindert, dass andere Benutzer auf Daten zugreifen, während Sie gesperrt sind|  
|**adlockoptimistisch**|-Andere Benutzer können auf Daten zugreifen.|-Daten können von mehreren Benutzern gleichzeitig geändert werden.|
