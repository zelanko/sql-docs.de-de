---
description: Erstellen von Variablen Wert Dateien (accesstosql)
title: Erstellen von Variablen Wert Dateien (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 4b8f84909de05efc5d53b924eb298adcaab93d7f
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91985033"
---
# <a name="creating-variable-value-files-accesstosql"></a>Erstellen von Variablen Wert Dateien (accesstosql)
Eine Variablen Wert Datei ist eine XML-Datei, die die Parameterwerte von Befehlen (z. b. der Quell-oder Zielserver Name) umfasst, die sich häufig über Server Migrationen hinweg ändern. Wenn eine große Anzahl von Datenbankmigrationen auftritt, werden mehrere Variablen Dateien zum Speichern des Werts jedes Quell Servers erstellt und in einer Master Skriptdatei mit dem Schalter **-v** in der Befehlszeile referenziert. Dieses Verhalten trägt dazu bei, statische Werte in einigen Skriptdateien mit den Variablen Werten in mehreren Variablen Dateien beizubehalten.  
  
> [!NOTE]  
> -  Variablennamen wird ein Präfix mit einem Suffix von $ (Dollar) vorangestellt. Wenn einer Variablen in der Variablen Wert Datei kein Wert zugewiesen wird, tritt ein Fehler während der Verarbeitung der Skriptdatei auf, was dazu führt, dass der Konsolen Ausführungsprozess beendet wird.  
> -  Das Escapezeichen für **$** ist **$$** . Wenn der Wert einer Variablen oder eines statischen Werts eines Parameters ein **$** (Dollar-) Symbol enthält, **$$** muss angegeben werden, um ihn als Zeichen anstelle einer Variablen zu behandeln.  
> -  Aus Gründen der Wartbarkeit können Variablen in- `'variable-group'` Elementen für die logische Trennung von benutzerdefinierten Variablen deklariert werden.  Die Verwendung dieses Elements ist nicht obligatorisch.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
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
  
## <a name="variable-value-file-validation"></a>Überprüfung der Variablen Wert Datei  
Der Benutzer kann die Datei mit den Variablen Werten auf einfache Weise anhand der Schema Definitionsdatei **consolescriptvariablesschema. xsd** überprüfen, die im Ordner "Schemas" verfügbar ist.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Betriebs Konsole besteht darin, [die Server Verbindungs Dateien &#40;Access Token zu erstellen&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen der Server Verbindungs Dateien (Access)](./creating-the-server-connection-files-accesstosql.md)  
