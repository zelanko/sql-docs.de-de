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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ddb695d996cdd40b7fde4087799e5c1ec84224c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081932"
---
# <a name="create-index-statement-limitations"></a>Einschränkungen der CREATE INDEX-Anweisung
Die CREATE INDEX-Anweisung wird für Microsoft Excel-oder Text-Treiber nicht unterstützt.  
  
 Ein Index kann für maximal 10 Spalten definiert werden. Wenn mehr als 10 Spalten in einer CREATE INDEX-Anweisung enthalten sind, wird der Index nicht erkannt, und die Tabelle wird so behandelt, als ob kein Index erstellt wurde.  
  
 Der dBase-Treiber kann keinen Index für eine logische Spalte erstellen.  
  
 Wenn der dBase-Treiber verwendet wird, kann die Reaktionszeit für große Dateien verbessert werden, indem ein MDX-Index (oder NDX-Index) für die Spalte (Feld), die in den WHERE-Klauseln einer SELECT-Anweisung angegeben ist, festgelegt wird. Vorhandene MDX-Indizes werden automatisch für =, >, \<>= =, =< und zwischen Operatoren in einer WHERE-Klausel, wie z. b. Prädikaten und in joinprädikaten angewendet.  
  
 Wenn der dBase-Treiber verwendet wird, ist der von einer CREATE UNIQUE Index-Anweisung erstellte Index tatsächlich nicht eindeutig, und doppelte Werte können in die indizierte Spalte eingefügt werden. Dem Index kann nur ein Datensatz aus einer Gruppe mit identischen Schlüsselwerten hinzugefügt werden.  
  
 Wenn der Paradox-Treiber verwendet wird, muss ein eindeutiger Index für eine zusammenhängende Teilmenge der Spalten in einer Tabelle definiert werden, einschließlich der ersten Spalte. Eine Tabelle kann nicht vom Paradox-Treiber aktualisiert werden, wenn kein eindeutiger Index für die Tabelle definiert ist oder wenn der Paradox-Treiber ohne die Implementierung des Borland-Datenbank-Engine verwendet wird.
