---
title: Vom Assistenten zum Generieren von Skripts unterstützte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58e3aa77c7c21b89917c23c80f42330442863a18
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66063931"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Vom Assistenten zum Generieren von Skripts unterstützte Objekte
  Der Assistent zum Generieren und Veröffentlichen von Skripts unterstützt eine Teilmenge der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]unterstützten Objekte.  
  
## <a name="supported-objects"></a>Unterstützte Objekte  
 In der folgenden Tabelle finden Sie die Objekte, die vom Assistenten zum Generieren und Veröffentlichen von Skripts veröffentlicht werden können.  
  
||||||  
|-|-|-|-|-|  
|Anwendungsrolle|Datenbankrolle|Schema|Benutzerdefiniertes Aggregat|Ansicht<sup>1</sup>|  
|Assembly|DEFAULT-Einschränkung|Gespeicherte Prozedur<sup>1</sup>|Benutzerdefinierter Datentyp|XML-Schemaauflistung|  
|CHECK-Einschränkung|Volltextkatalog|Synonym|Benutzerdefinierte Funktion||  
|CLR (common Language Runtime)-Prozedur<sup>1</sup>|Index|Tabelle|Benutzerdefinierte Tabelle||  
|CLR-benutzerdefinierte Funktion|Rule|Benutzer<sup>2</sup>|Benutzerdefinierter Typ||  
  
 <sup>1</sup> ohne Verschlüsselung veröffentlicht.  
  
 <sup>2</sup> alle nicht-System-Benutzer, die in der Datenbank vorhanden, werden als Rollen veröffentlicht.  
  
  
