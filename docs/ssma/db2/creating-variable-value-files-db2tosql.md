---
title: Erstellen von Variablen Wert Dateien (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 945b7e86641c796e79bfb87b8b7b5de25949e4c2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67989767"
---
# <a name="creating-variable-value-files-db2tosql"></a>Erstellen von Variablen Wert Dateien (DB2ToSQL)
Die Variable Wert Datei ist eine XML-Datei, die die Parameterwerte von Befehlen wie, dem Quell-oder Zielserver Namen, der sich häufig von einer Servermigration in eine andere ändert, umfasst. Wenn eine große Anzahl von Datenbankmigrationen auftritt, werden mehrere Variablen Dateien zum Speichern des Werts jedes Quell Servers erstellt und in einer Master Skriptdatei mit dem Schalter **-v** in der Befehlszeile referenziert. Dies trägt dazu bei, statische Werte in einigen Skriptdateien mit den Variablen Werten in mehreren Variablen Dateien beizubehalten.  
  
> [!NOTE]  
> 1.  Variablennamen wird ein Präfix mit einem Suffix von $ (Dollar) vorangestellt. Wenn den Variablen kein Wert in der Variablen Wert Datei zugewiesen wird, tritt bei der Verarbeitung der Skriptdatei ein Fehler auf, der dazu führt, dass der Konsolen Ausführungsprozess beendet wird.  
> 2.  Das Escapezeichen **$** für **$$** ist. Wenn der Wert einer Variablen oder eines statischen Werts eines Parameters das **$** Symbol (Dollar) enthält, **$$** muss angegeben werden, um ihn als Zeichen anstelle einer Variablen zu behandeln.  
> 3.  Aus Gründen der Wartbarkeit können Variablen in `'variable-group'` -Elementen für die logische Trennung von benutzerdefinierten Variablen deklariert werden.  Die Verwendung dieses Elements ist nicht obligatorisch.  
  
**Beispiele:**  
  
**Beispiel 1:**  
  
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
Der nächste Schritt bei der Betriebs Konsole besteht darin, [die Server Verbindungs Dateien &#40;DB2ToSQL zu erstellen&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen der Serververbindungsdateien](../oracle/creating-the-server-connection-files-oracletosql.md)  
  
