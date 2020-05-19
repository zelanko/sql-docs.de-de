---
title: Vom Assistenten zum Generieren von Skripts unterstützte Objekte
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1cfee492433da4a9812a6961d34b741cf8bff089
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703825"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Vom Assistenten zum Generieren von Skripts unterstützte Objekte
  Der Assistent zum Generieren und Veröffentlichen von Skripts unterstützt eine Teilmenge der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]unterstützten Objekte.  
  
## <a name="supported-objects"></a>Unterstützte Objekte  
 In der folgenden Tabelle finden Sie die Objekte, die vom Assistenten zum Generieren und Veröffentlichen von Skripts veröffentlicht werden können.  
  
||||||  
|-|-|-|-|-|  
|Anwendungsrolle|Datenbankrolle|Schema|Benutzerdefiniertes Aggregat|Sicht<sup>1</sup>|  
|Assembly|DEFAULT-Einschränkung|Gespeicherte Prozedur<sup>1</sup>|Benutzerdefinierter Datentyp|XML-Schemaauflistung|  
|CHECK-Einschränkung|Volltextkatalog|Synonym|Benutzerdefinierte Funktion||  
|Gespeicherte CLR-Prozedur (Common Language Runtime)<sup>1</sup>|Index|Tabelle|Benutzerdefinierte Tabelle||  
|CLR-benutzerdefinierte Funktion|Regel|Benutzer<sup>2</sup>|Benutzerdefinierter Typ||  
  
 <sup>1</sup> ohne Verschlüsselung veröffentlicht.  
  
 <sup>2</sup> alle nicht-Systembenutzer, die in der-Datenbank vorhanden sind, werden als Rollen veröffentlicht.  
  
  
