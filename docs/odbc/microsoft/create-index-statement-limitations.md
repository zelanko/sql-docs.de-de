---
title: Einschränkungen der CREATE INDEX-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 053287d5087b377429221c31dd4e6b20f24248e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280881"
---
# <a name="create-index-statement-limitations"></a>Einschränkungen der CREATE INDEX-Anweisung
Die CREATE INDEX-Anweisung wird für Microsoft Excel-oder Text-Treiber nicht unterstützt.  
  
 Ein Index kann für maximal 10 Spalten definiert werden. Wenn mehr als 10 Spalten in einer CREATE INDEX-Anweisung enthalten sind, wird der Index nicht erkannt, und die Tabelle wird so behandelt, als ob kein Index erstellt wurde.  
  
 Der dBase-Treiber kann keinen Index für eine logische Spalte erstellen.  
  
 Wenn der dBase-Treiber verwendet wird, kann die Reaktionszeit für große Dateien verbessert werden, indem ein MDX-Index (oder NDX-Index) für die Spalte (Feld), die in den WHERE-Klauseln einer SELECT-Anweisung angegeben ist, festgelegt wird. Vorhandene MDX-Indizes werden automatisch für =, >, \<>= =, =< und zwischen Operatoren in einer WHERE-Klausel, wie z. b. Prädikaten und in joinprädikaten angewendet.  
  
 Wenn der dBase-Treiber verwendet wird, ist der von einer CREATE UNIQUE Index-Anweisung erstellte Index tatsächlich nicht eindeutig, und doppelte Werte können in die indizierte Spalte eingefügt werden. Dem Index kann nur ein Datensatz aus einer Gruppe mit identischen Schlüsselwerten hinzugefügt werden.  
  
 Wenn der Paradox-Treiber verwendet wird, muss ein eindeutiger Index für eine zusammenhängende Teilmenge der Spalten in einer Tabelle definiert werden, einschließlich der ersten Spalte. Eine Tabelle kann nicht vom Paradox-Treiber aktualisiert werden, wenn kein eindeutiger Index für die Tabelle definiert ist oder wenn der Paradox-Treiber ohne die Implementierung des Borland-Datenbank-Engine verwendet wird.
