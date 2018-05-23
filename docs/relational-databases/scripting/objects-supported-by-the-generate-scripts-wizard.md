---
title: Vom Assistenten zum Generieren von Skripts unterstützte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9bea6568c2ea38458a26aba277eab7c1a3ffac56
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Vom Assistenten zum Generieren von Skripts unterstützte Objekte
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Der Assistent zum Generieren und Veröffentlichen von Skripts unterstützt eine Teilmenge der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]unterstützten Objekte.  
  
## <a name="supported-objects"></a>Unterstützte Objekte  
 In der folgenden Tabelle finden Sie die Objekte, die vom Assistenten zum Generieren und Veröffentlichen von Skripts veröffentlicht werden können.  
  
||||||  
|-|-|-|-|-|  
|Anwendungsrolle|Datenbankrolle|Schema|Benutzerdefiniertes Aggregat|Sicht*|  
|Assembly|DEFAULT-Einschränkung|Gespeicherte Prozedur*|Benutzerdefinierter Datentyp|XML-Schemaauflistung|  
|CHECK-Einschränkung|Volltextkatalog|Synonym|Benutzerdefinierte Funktion||  
|CLR-gespeicherte Prozedur (Common Language Runtime)*|Index|Tabelle|Benutzerdefinierte Tabelle||  
|CLR-benutzerdefinierte Funktion|Regel|Benutzer**|Benutzerdefinierter Typ||  
  
 *Ohne Verschlüsselung veröffentlicht.  
  
 **Alle Nicht-Systembenutzer in der Datenbank werden als Rollen veröffentlicht.  
  
  
