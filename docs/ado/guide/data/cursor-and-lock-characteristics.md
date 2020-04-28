---
title: Cursor-und Sperr Merkmale | Microsoft-Dokumentation
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
ms.openlocfilehash: c4d6f86539e1abc7ee74087b130e0186322346e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925675"
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
