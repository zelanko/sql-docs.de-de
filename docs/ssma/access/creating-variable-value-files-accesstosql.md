---
title: Erstellen die Variable Value Files (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 00144c51e60b72fe043443d2a9c8d1d51a6cb8da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138832"
---
# <a name="creating-variable-value-files-accesstosql"></a>Erstellen die Variable Value Files (AccessToSQL)
Eine Variable-Datei ist eine XML-Datei mit die Werte der Parameter der Befehle (z. B. die Quelle oder Ziel-Servername), die häufig in Server-Migrationen zu ändern. Wenn eine große Anzahl von datenbankmigrationen auftreten, mehrere Dateien zum Speichern von den Wert der einzelnen Quellserver erstellt und auf die verwiesen wird in einer master-Skript-Datei mit den **- V** -Schalter an der Befehlszeile. Dies hilft bei der Verwaltung von statische Werte in ein paar Skriptdateien mit der Variablenwerte in mehrere Dateien.  
  
> [!NOTE]  
> -  Namen von Variablen sind mit dem Präfix und Suffix mit einem Symbol $ (Dollarzeichen). Wenn eine Variable einen Wert in der Datei der Wert der Variablen nicht zugewiesen ist, tritt ein Fehler während der Analyse der Skriptdatei, wodurch treten des Ausführungsprozess der Konsole.  
> -  Das Escapezeichen für **$** ist **$$**. Wenn der Wert einer Variable oder ein statischer Wert eines Parameters enthält eine **$** (Dollar)-Symbol, klicken Sie dann **$$** muss angegeben werden, um diese als Zeichen und keiner Variablen zu behandeln.  
> -  Aus Gründen der Verwaltbarkeit können in Variablen deklariert werden `'variable-group'` Elemente für die logische Trennung von benutzerdefinierten Variablen.  Verwendung dieses Elements ist nicht erforderlich.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**Beispiel 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>Variablenwert-dateiüberprüfung  
Benutzer kann ganz einfach überprüfen, seinen Wert der Variablen-Datei anhand der Schemadefinitionsdatei **ConsoleScriptVariablesSchema.xsd** in den Ordner "Schemas" verfügbar.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [erstellen den Server Connection Files &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen den Server Connection Files (Datenzugriff)](https://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
