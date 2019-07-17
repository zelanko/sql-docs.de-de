---
title: Erstellen die Variable Value Files (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 87db0ebd006e2ca87ddc4744a4bbcd396a827712
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266125"
---
# <a name="creating-variable-value-files-oracletosql"></a>Erstellen von Variablenwertdateien (OracleToSQL)
Variablendatei Wert ist eine XML-Datei mit die Werte der Parameter der Befehle wie die Quelle oder Ziel-Servername, die häufig von der Migration von einem Server auf einen anderen ändern. Wenn eine große Anzahl von datenbankmigrationen auftreten, mehrere Dateien zum Speichern von den Wert der einzelnen Quellserver werden erstellt und auf die verwiesen wird in einer master-Skript-Datei mit den **- V** -Schalter an der Befehlszeile. Dies hilft beim Verwalten von statischer Werten in ein paar Skriptdateien mit den Variablen Werten in mehreren Dateien.  
  
> [!NOTE]  
> 1.  Namen von Variablen sind mit dem Präfix und Suffix mit einem Symbol $ (Dollarzeichen). Wenn die Variablen einen Wert in der Datei der Wert der Variablen nicht zugewiesen sind, werden Sie ein Fehler auftritt, während der Analyse der Skriptdatei an, was in der Konsole Ausführungsprozess treten.  
> 2.  Das Escapezeichen für **$** ist **$$** . Wenn der Wert einer Variable oder ein statischer Wert eines Parameters enthält **$** (Dollar)-Symbol, klicken Sie dann **$$** muss angegeben werden, um diese als Zeichen und keiner Variablen zu behandeln.  
> 3.  Aus Gründen der Verwaltbarkeit können in Variablen deklariert werden `'variable-group'` Elemente für die logische Trennung von Benutzer definierten Variablen.  Verwendung dieses Elements ist nicht erforderlich.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Beispiel 2:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [erstellen den Server Connection Files &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen die Server-Datenbankdateien (Oracle)](https://msdn.microsoft.com/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
