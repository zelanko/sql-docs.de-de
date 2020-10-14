---
description: Erstellen von Variablenwertdateien (SybaseToSQL)
title: Erstellen von Variablen Wert Dateien (sybasedesql) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 2f2d3a53cb12a0d7762137a44cc12ec6f06a5d81
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036699"
---
# <a name="creating-variable-value-files-sybasetosql"></a>Erstellen von Variablenwertdateien (SybaseToSQL)
Die Variable Wert Datei ist eine XML-Datei, die die Parameterwerte von Befehlen wie, dem Quell-oder Zielserver Namen, der sich häufig von einer Servermigration in eine andere ändert, umfasst. Wenn eine große Anzahl von Datenbankmigrationen auftritt, werden mehrere Variablen Dateien zum Speichern des Werts jedes Quell Servers erstellt und in einer Master Skriptdatei mit dem Schalter **-v** in der Befehlszeile referenziert. Dies trägt dazu bei, statische Werte in einigen Skriptdateien mit den Variablen Werten in mehreren Variablen Dateien beizubehalten.  
  
> [!NOTE]  
> 1.  Variablennamen wird ein Präfix mit einem Suffix von $ (Dollar) vorangestellt. Wenn den Variablen kein Wert in der Variablen Wert Datei zugewiesen wird, tritt bei der Verarbeitung der Skriptdatei ein Fehler auf, der dazu führt, dass der Konsolen Ausführungsprozess beendet wird.  
> 2.  Das Escapezeichen für **$** ist **$$** . Wenn der Wert einer Variablen oder eines statischen Werts eines Parameters das **$** Symbol (Dollar) enthält, **$$** muss angegeben werden, um ihn als Zeichen anstelle einer Variablen zu behandeln.  
> 3.  Aus Gründen der Wartbarkeit können Variablen in- `'variable-group'` Elementen für die logische Trennung von benutzerdefinierten Variablen deklariert werden.  Die Verwendung dieses Elements ist nicht obligatorisch.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
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
  
## <a name="variable-value-file-validation"></a>Überprüfung der Variablen Wert Datei  
Der Benutzer kann die Datei mit den Variablen Werten auf einfache Weise anhand der Schema Definitionsdatei **consolescriptvariablesschema. xsd** überprüfen, die im Ordner "Schemas" verfügbar ist.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Betriebs Konsole besteht darin, [die Server Verbindungs Dateien &#40;sybasedesql zu erstellen&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen der Server Dateien (Sybase)](./creating-the-server-connection-files-sybasetosql.md)  
