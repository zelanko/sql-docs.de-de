---
title: Einschränkungen der CREATE INDEX Anweisung | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: ec6ba27197f7a6021aff90d30884129128cb3614
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837038"
---
# <a name="create-index-statement-limitations"></a>Einschränkungen der CREATE INDEX-Anweisung
CREATE INDEX-Anweisung wird für die Microsoft Excel- oder Textdateien Treiber nicht unterstützt.  
  
 Ein Index kann für maximal 10 Spalten definiert werden. Wenn mehr als 10 Spalten in einer CREATE INDEX-Anweisung enthalten sind, wird der Index wird nicht erkannt und in der Tabelle behandelt werden, als wäre kein Index erstellt wurden.  
  
 DBASE-Treiber kann nicht über einen Index für eine logische Spalte erstellen.  
  
 Wenn die dBASE-Treiber verwendet wird, kann die Antwortzeit für große Dateien verbessert werden, durch Erstellen eines Indexes MDX (oder NDX) in der Spalte (Feld) in der WHERE-Klausel einer SELECT-Anweisung angegeben. Vorhandene MDX-Indizes werden automatisch angewendet werden, für =, >, \<, > =, = <, Operatoren, die in einer WHERE-Klausel und LIKE-Prädikaten sowie in Join-Prädikate und BETWEEN.  
  
 Wenn die dBASE-Treiber verwendet wird, der durch eine CREATE UNIQUE INDEX-Anweisung erstellte Index ist tatsächlich nicht eindeutig, und doppelte Werte in der indizierten Spalte eingefügt werden können. Nur ein Datensatz aus einem Satz mit zwei identische Schlüsselwerte kann, die dem Index hinzugefügt werden.  
  
 Wenn die Paradox-Treiber verwendet wird, muss ein eindeutiger Index auf einer zusammenhängenden Teilmenge der Spalten in einer Tabelle, einschließlich der ersten Spalte definiert werden. Eine Tabelle kann nicht vom Paradox-Treiber aktualisiert werden, wenn Sie ein eindeutiger Index nicht definiert ist, für die Tabelle, oder wenn die Paradox-Treiber, ohne die Implementierung der Borland Datenbank-Engine verwendet wird.
