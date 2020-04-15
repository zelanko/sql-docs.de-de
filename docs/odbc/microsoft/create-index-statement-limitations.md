---
title: CREATE INDEX-Anweisungsbeschränkungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280881"
---
# <a name="create-index-statement-limitations"></a>Einschränkungen der CREATE INDEX-Anweisung
Die CREATE INDEX-Anweisung wird für die Microsoft Excel- oder Texttreiber nicht unterstützt.  
  
 Ein Index kann für maximal 10 Spalten definiert werden. Wenn mehr als 10 Spalten in einer CREATE INDEX-Anweisung enthalten sind, wird der Index nicht erkannt, und die Tabelle wird so behandelt, als ob kein Index erstellt wurde.  
  
 Der dBASE-Treiber kann keinen Index für eine LOGICAL-Spalte erstellen.  
  
 Wenn der dBASE-Treiber verwendet wird, kann die Antwortzeit für große Dateien verbessert werden, indem ein .mdx(oder .ndx)-Index für die Spalte (Feld) in der Spalte (Feld) hergestellt wird, die in den WHERE-Klauseln einer SELECT-Anweisung angegeben ist. Vorhandene .mdx-Indizes werden automatisch für =, >, \<, >=, =< und BETWEEN-Operatoren in einer WHERE-Klausel und LIKE-Prädikaten sowie in Join-Prädikaten angewendet.  
  
 Wenn der dBASE-Treiber verwendet wird, ist der von einer CREATE UNIQUE INDEX-Anweisung erstellte Index eigentlich nicht eindeutig, und doppelte Werte können in die indizierte Spalte eingefügt werden. Dem Index kann nur ein Datensatz aus einem Satz mit identischen Schlüsselwerten hinzugefügt werden.  
  
 Wenn der Paradox-Treiber verwendet wird, muss ein eindeutiger Index für eine zusammenhängende Teilmenge der Spalten in einer Tabelle definiert werden, einschließlich der ersten Spalte. Eine Tabelle kann vom Paradox-Treiber nicht aktualisiert werden, wenn kein eindeutiger Index in der Tabelle definiert ist oder wenn der Paradox-Treiber ohne die Implementierung der Borland Database Engine verwendet wird.
