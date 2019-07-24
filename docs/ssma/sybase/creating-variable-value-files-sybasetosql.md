---
title: Erstellen die Variable Value Files (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Creating Variable Value Files
- Sybase Console,Variable Value File Validation
ms.assetid: 395be464-4b19-44f7-91e5-b8876d6743dc
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2c0c76a36502d9d590b6db478efcab6feb50ba01
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029388"
---
# <a name="creating-variable-value-files-sybasetosql"></a>Erstellen von Variablenwertdateien (SybaseToSQL)
Variablendatei Wert ist eine XML-Datei mit die Werte der Parameter der Befehle wie die Quelle oder Ziel-Servername, die häufig von der Migration von einem Server auf einen anderen ändern. Wenn eine große Anzahl von datenbankmigrationen auftreten, mehrere Dateien zum Speichern von den Wert der einzelnen Quellserver werden erstellt und auf die verwiesen wird in einer master-Skript-Datei mit den **- V** -Schalter an der Befehlszeile. Dies hilft beim Verwalten von statischer Werten in ein paar Skriptdateien mit den Variablen Werten in mehreren Dateien.  
  
> [!NOTE]  
> 1.  Namen von Variablen sind mit dem Präfix und Suffix mit einem Symbol $ (Dollarzeichen). Wenn die Variablen einen Wert in der Datei der Wert der Variablen nicht zugewiesen sind, werden Sie ein Fehler auftritt, während der Analyse der Skriptdatei an, was in der Konsole Ausführungsprozess treten.  
> 2.  Das Escapezeichen für **$** ist **$$** . Wenn der Wert einer Variable oder ein statischer Wert eines Parameters enthält **$** (Dollar)-Symbol, klicken Sie dann **$$** muss angegeben werden, um diese als Zeichen und keiner Variablen zu behandeln.  
> 3.  Aus Gründen der Verwaltbarkeit können in Variablen deklariert werden `'variable-group'` Elemente für die logische Trennung von Benutzer definierten Variablen.  Verwendung dieses Elements ist nicht erforderlich.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
```xml  
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
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
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
  
## <a name="variable-value-file-validation"></a>Variablenwert-Dateiüberprüfung  
Benutzer kann ganz einfach überprüfen, seinen Wert der Variablen-Datei anhand der Schemadefinitionsdatei **ConsoleScriptVariablesSchema.xsd** in den Ordner "Schemas" verfügbar.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [erstellen den Server Connection Files &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen die Server-Datenbankdateien (Sybase)](https://msdn.microsoft.com/35ef396f-9f98-429d-9fc5-4f413d08fb37)  
  
