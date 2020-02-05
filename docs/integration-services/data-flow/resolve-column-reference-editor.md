---
title: Editor zum Auflösen von Spaltenverweisen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4340dfcaa7807616ccd8c3cdf4e504d0e33423c0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298119"
---
# <a name="resolve-column-reference-editor"></a>Editor zum Auflösen von Spaltenverweisen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Wenn ein Eingabepfad getrennt wurde, oder nicht zugeordnete Spalten im Pfad vorhanden sind, wird neben dem entsprechenden Datenpfad ein Fehlersymbol angezeigt. Der Editor zum Auflösen von Verweisen ermöglicht, für alle Pfade in der Ausführungsstruktur nicht zugeordnete Ausgabespalten mit nicht zugeordneten Eingabespalten zu verknüpfen, und vereinfacht dadurch die Lösung von Spaltenverweisfehlern. Der Editor zum Auflösen von Verweisen markiert auch die Pfade, um zu kennzeichnen, welche Pfade aufgelöst werden.  
  
> [!NOTE]  
>  Es ist möglich, eine Komponente auch dann zu bearbeiten, wenn deren Eingabepfad getrennt ist.  
  
 Nachdem alle Spaltenverweise aufgelöst wurden und keine weiteren Datenpfadfehler auftreten, werden neben den Datenpfaden keine Fehlersymbole angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Nicht zugeordnete Ausgabespalten (Quelle)**     
 Spalten vom Upstreampfad, die derzeit nicht zugeordnet sind.  
  
**Zugeordnete Spalten (Quelle)**     
 Spalten vom Upstreampfad, die Spalten vom Downstreampfad zugeordnet sind.  
  
**Zugeordnete Spalten (Ziel)**     
 Spalten vom Upstreampfad, die Spalten vom Downstreampfad zugeordnet sind.  
  
**Nicht zugeordnete Eingabespalten (Ziel)**     
 Spalten vom Downstreampfad, die derzeit nicht zugeordnet sind.  
  
**Nicht zugeordnete Eingabespalten löschen**  
 Aktivieren Sie "Nicht zugeordnete Eingabespalten löschen", um nicht zugeordnete Spalten am Ziel des Datenpfads zu ignorieren. Die Schaltfläche "Vorschau der Änderungen" zeigt eine Liste der Änderungen an, die auftreten, wenn Sie auf die Schaltfläche "OK" klicken.  
  
  
