---
title: Benutzerdefinierte Eigenschaften von Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8d556a199b608659a9ceaaeb3b7036155886d6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827233"
---
# <a name="excel-custom-properties"></a>Benutzerdefinierte Eigenschaften von Excel
  **Benutzerdefinierte Eigenschaften von Quellen**  
  
 Die Excel-Quelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der Excel-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|Der zum Zugreifen auf die Datenbank verwendete Modus. Mögliche Werte sind **Open Rowset**, **Open Rowset from Variable**, `SQL Command`und **SQL command from Variable**. Der Standardwert ist **Geöffnetes Rowset**.|  
|CommandTimeout|Integer|Die Anzahl der Sekunden, nach denen ein Befehl wegen eines Timeouts abgebrochen wird.  Der Wert 0 steht für ein unbegrenztes Timeout.<br /><br /> **Hinweis** Diese Eigenschaft ist nicht im **Quellen-Editor für Excel**verfügbar, kann jedoch mit dem Dialogfeld **Erweiterter Editor**festgelegt werden.|  
|OpenRowset|String|Der Name des Datenbankobjekts, das zum Öffnen eines Rowsets verwendet wird.|  
|OpenRowsetVariable|String|Die Variable, die den Namen des Datenbankobjekts enthält, das zum Öffnen eines Rowsets verwendet wird.|  
|ParameterMapping|String|Die Zuordnung von Parametern im SQL-Befehl zu Variablen.|  
|SqlCommand|String|Der auszuführende SQL-Befehl.|  
|SqlCommandVariable|String|Die Variable, die den auszuführenden SQL-Befehl enthält.|  
  
 Die Ausgabe und die Ausgabespalten der Excel-Quelle verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Excel Source](excel-source.md).  
  
 **Benutzerdefinierte Eigenschaften von Zielen**  
  
 Das Excel-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Excel-Ziels. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Ein Wert, der angibt, wie das Ziel auf seine Zieldatenbank zugreift.<br /><br /> Diese Eigenschaft kann einen der folgenden Werte haben:<br /><br /> `OpenRowset`(0): Geben Sie den Namen einer Tabelle oder Sicht an.<br /><br /> `OpenRowset from Variable`(1): Geben Sie den Namen einer Variablen an, die den Namen einer Tabelle oder Sicht enthält.<br /><br /> `OpenRowset Using Fastload`(3): Sie geben den Namen einer Tabelle oder Sicht an.<br /><br /> `OpenRowset Using Fastload from Variable`(4): Geben Sie den Namen einer Variablen an, die den Namen einer Tabelle oder Sicht enthält.<br /><br /> `SQL Command`(2): Sie geben eine SQL-Anweisung an.|  
|CommandTimeout|Integer|Die maximale Ausführungsdauer in Sekunden, bevor ein Timeout für den SQL-Befehl eintritt. Der Wert **0** gibt einen unbegrenzten Zeitraum an. Der Standardwert dieser Eigenschaft ist **0**.<br /><br /> Hinweis: Diese Eigenschaft ist nicht im **Ziel-Editor für Excel** verfügbar, kann jedoch mit dem **Erweiterten Editor** festgelegt werden.|  
|FastLoadKeepIdentity|Boolean|Ein Wert, der angibt, ob Identitätswerte beim Laden von Daten kopiert werden sollen. Diese Eigenschaft ist nur verfügbar, wenn eine der Optionen für das schnelle Laden verwendet wird. Der Standardwert dieser Eigenschaft ist **False**.|  
|FastLoadKeepNulls|Boolean|Ein Wert, der angibt, ob NULL-Werte beim Laden von Daten kopiert werden sollen. Diese Eigenschaft ist nur verfügbar, wenn eine der Optionen für das schnelle Laden verwendet wird. Der Standardwert dieser Eigenschaft ist **False**.|  
|FastLoadMaxInsertCommitSize|Integer|Ein Wert, der die Batchgröße angibt, für die das Excel-Ziel bei schnellen Ladevorgängen die Durchführung eines Commits versucht. Der Standardwert ist **2147483647**. Der Wert **0** gibt einen einzelnen Commitvorgang an, nachdem alle Zeilen verarbeitet wurden.|  
|FastLoadOptions|String|Eine Auflistung von Optionen für schnelles Laden. Die Optionen für schnelles Laden beinhalten das Sperren von Tabellen und die Überprüfung von Einschränkungen. Sie können eines, beides oder keines von beiden angeben.<br /><br /> Hinweis: Einige Optionen für diese Eigenschaft sind nicht im **Ziel-Editor für Excel** verfügbar, können jedoch mit dem **Erweiterten Editor** festgelegt werden.|  
|OpenRowset|String|Wenn Access Mode auf `OpenRowset`festgelegt ist, der Name der Tabelle oder Sicht, auf die das Excel-Ziel zugreift.|  
|OpenRowsetVariable|String|Wenn Access Mode auf `OpenRowset from Variable`festgelegt ist, der Name der Variablen, die den Namen der Tabelle oder Sicht enthält, auf die das Excel-Ziel zugreift.|  
|SqlCommand|String|Wenn Access Mode auf `SQL Command`festgelegt ist, gibt die Transact-SQL-Anweisung, die das Excel-Ziel verwendet, die Ziel Spalten für die Daten an.|  
  
 Die Eingabe und die Eingabespalten des Excel-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Excel Destination](excel-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](../common-properties.md)  
  
  
