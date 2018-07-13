---
title: Benutzerdefinierte Eigenschaften von Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 34fe10fcfbfde6494ff1b2a354d3958ac65e372c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235290"
---
# <a name="excel-custom-properties"></a>Benutzerdefinierte Eigenschaften von Excel
  **Benutzerdefinierte Eigenschaften von Quellen**  
  
 Die Excel-Quelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der Excel-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|Der zum Zugreifen auf die Datenbank verwendete Modus. Die möglichen Werte sind **geöffnetes Rowset**, **geöffnetes Rowset aus Variable**, `SQL Command`, und **SQL-Befehl aus Variable**. Der Standardwert ist **Geöffnetes Rowset**.|  
|CommandTimeout|Integer|Die Anzahl der Sekunden, nach denen ein Befehl wegen eines Timeouts abgebrochen wird.  Der Wert 0 steht für ein unbegrenztes Timeout.<br /><br /> **Hinweis** Diese Eigenschaft ist nicht im **Quellen-Editor für Excel**verfügbar, kann jedoch mit dem Dialogfeld **Erweiterter Editor**festgelegt werden.|  
|OpenRowset|Zeichenfolge|Der Name des Datenbankobjekts, das zum Öffnen eines Rowsets verwendet wird.|  
|OpenRowsetVariable|Zeichenfolge|Die Variable, die den Namen des Datenbankobjekts enthält, das zum Öffnen eines Rowsets verwendet wird.|  
|ParameterMapping|Zeichenfolge|Die Zuordnung von Parametern im SQL-Befehl zu Variablen.|  
|SqlCommand|Zeichenfolge|Der auszuführende SQL-Befehl.|  
|SqlCommandVariable|Zeichenfolge|Die Variable, die den auszuführenden SQL-Befehl enthält.|  
  
 Die Ausgabe und die Ausgabespalten der Excel-Quelle verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Excel Source](excel-source.md).  
  
 **Benutzerdefinierte Eigenschaften von Zielen**  
  
 Das Excel-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Excel-Ziels. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Ein Wert, der angibt, wie das Ziel auf seine Zieldatenbank zugreift.<br /><br /> Diese Eigenschaft kann einen der folgenden Werte haben:<br /><br /> `OpenRowset` (0) – Sie geben den Namen einer Tabelle oder Sicht.<br /><br /> `OpenRowset from Variable` (1) – Sie geben den Namen einer Variablen, die den Namen einer Tabelle oder Sicht enthält.<br /><br /> `OpenRowset Using Fastload` (3) – Sie geben den Namen einer Tabelle oder Sicht an.<br /><br /> `OpenRowset Using Fastload from Variable` (4) – Sie geben den Namen einer Variablen, die den Namen einer Tabelle oder Sicht enthält.<br /><br /> `SQL Command` (2) - Sie geben eine SQL-Anweisung.|  
|CommandTimeout|Integer|Die maximale Ausführungsdauer in Sekunden, bevor ein Timeout für den SQL-Befehl eintritt. Der Wert **0** gibt einen unbegrenzten Zeitraum an. Der Standardwert dieser Eigenschaft ist **0**.<br /><br /> Hinweis: Diese Eigenschaft ist nicht im **Ziel-Editor für Excel**verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|FastLoadKeepIdentity|Boolean|Ein Wert, der angibt, ob Identitätswerte beim Laden von Daten kopiert werden sollen. Diese Eigenschaft ist nur verfügbar, wenn eine der Optionen für das schnelle Laden verwendet wird. Der Standardwert dieser Eigenschaft ist **False**.|  
|FastLoadKeepNulls|Boolean|Ein Wert, der angibt, ob NULL-Werte beim Laden von Daten kopiert werden sollen. Diese Eigenschaft ist nur verfügbar, wenn eine der Optionen für das schnelle Laden verwendet wird. Der Standardwert dieser Eigenschaft ist **False**.|  
|FastLoadMaxInsertCommitSize|Integer|Ein Wert, der die Batchgröße angibt, für die das Excel-Ziel bei schnellen Ladevorgängen die Durchführung eines Commits versucht. Der Standardwert ist **2147483647**. Der Wert **0** gibt einen einzelnen Commitvorgang an, nachdem alle Zeilen verarbeitet wurden.|  
|FastLoadOptions|Zeichenfolge|Eine Auflistung von Optionen für schnelles Laden. Die Optionen für schnelles Laden beinhalten das Sperren von Tabellen und die Überprüfung von Einschränkungen. Sie können eines, beides oder keines von beiden angeben.<br /><br /> Hinweis: Einige Optionen für diese Eigenschaft sind nicht im **Ziel-Editor für Excel**verfügbar, können jedoch mit dem **erweiterten Editor**festgelegt werden.|  
|OpenRowset|Zeichenfolge|Wenn AccessMode ist `OpenRowset`, den Namen der Tabelle oder Sicht, auf das Excel-Ziel zugreift.|  
|OpenRowsetVariable|Zeichenfolge|Wenn AccessMode ist `OpenRowset from Variable`, den Namen der Variablen mit dem Namen der Tabelle oder Sicht, auf das Excel-Ziel zugreift.|  
|SqlCommand|Zeichenfolge|Wenn AccessMode ist `SQL Command`, die Transact-SQL-Anweisung, das Excel-Ziel die Zielspalten für die Daten angibt.|  
  
 Die Eingabe und die Eingabespalten des Excel-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Excel Destination](excel-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  
