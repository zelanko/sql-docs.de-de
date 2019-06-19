---
title: Erstellen die Variable Value Files (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cf62d09de1180687598d817ff9199d7098008829
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299143"
---
# <a name="creating-variable-value-files-db2tosql"></a>Erstellen die Variable Value Files (DB2ToSQL)
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
Der nächste Schritt in der Konsole ausgeführt wird [erstellen den Server Connection Files &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Creating the Server Connection Files (Erstellen der Serververbindungsdateien)](../oracle/creating-the-server-connection-files-oracletosql.md)  
  
