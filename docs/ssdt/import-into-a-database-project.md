---
title: Importieren in ein Datenbankprojekt | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.SQLPROJECTIMPORTSNAPSHOTSUMMARYDIALOG.DIALOG
- SQL.DATA.TOOLS.SQLPROJECTIMPORTDATABASESUMMARYDIALOG.DIALOG
- SQL.DATA.TOOLS.IMPORTSCRIPTWIZARD.SUMMARY
ms.assetid: d0a0a394-6cb6-416a-a25f-9babf8ba294a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: af8ee2d569c44d19e518c1dafacddb958c66cc88
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087742"
---
# <a name="import-into-a-database-project"></a>Importieren in ein Datenbankprojekt
Mithilfe von Importieren können Sie ein Projekt mit neuen Objekten aus einer Livedatenbank oder einer DACPAC-Datei auffüllen bzw. im Projekt vorhandene Objekte anhand einer neuen Definition aus einem Skript aktualisieren. Bei den drei nachfolgend beschriebenen Methoden sind einige Verhaltensunterschiede zu beachten.  
  
**Menü „Importieren“**  
  
![SSDT-Menü „Importieren“](../ssdt/media/ssdt-import.gif "SSDT-Menü „Importieren“")  
  
**Abschnitte in diesem Thema**  
  
[Importquelle: Datenbank oder Datenschichtanwendung (DACPAC)](#bkmk_import_source_db)  
  
[Importquelle: Skript (SQL)](#bkmk_import_source_script)  
  
[Importieren verschlüsselter Objekte](#bkmk_import_encrypted)  
  
## <a name="bkmk_import_source_db"></a>Importquelle: Datenbank oder Datenschichtanwendung (DACPAC)  
Die Fähigkeit, ein Schema aus einer Datenbank oder DACPAC-Datei zu importieren, ist nur verfügbar, wenn noch keine Schemaobjekte im Projekt definiert sind. Davon ausgeschlossen sind RefactorLog-Dateien oder Skripts vor und nach der Bereitstellung.  
  
Beim Import werden für Objektdefinitionen Skripts in Projektdateien erstellt, wobei die in SSDT enthaltenen betrieblichen Standardwerte für neue Objekte verwendet werden: neue Dateien für Objekte oberster Ebene, untergeordnete Hierarchieelemente, die in derselben Datei wie das übergeordnete Element definiert sind, oder inline definierte Tabellen- oder Spalteneinschränkungen (sofern möglich). Um die Sichtbarkeit und Steuerung der einzelnen Objekte zu verbessern, verwenden Sie anstelle von Importieren die Option Schemavergleich.  
  
Wenn die Importquelle Skripts vor und nach der Bereitstellung, RefactorLog-Dateien oder Definitionen von SQLCMD-Variablen enthält, werden diese in das Projekt importiert. Wenn eines dieser Artefakte bereits im Projekt enthalten ist, werden die importierten Dateien einem Projektordner namens **Beim Import ignoriert** hinzugefügt.  
  
**Ordner „Beim Import ignoriert“**  
  
![SSDT-Ordner „Beim Import ignoriert“](../ssdt/media/ssdt-ignoredonimport.gif "SSDT-Ordner „Beim Import ignoriert“")  
  
## <a name="bkmk_import_source_script"></a>Importquelle: Skript (SQL)  
Alle Objekte aus der Importquelle, die *noch nicht* im Projekt enthalten sind, werden hinzugefügt. Demgegenüber wird die Objektdefinition von allen Objekten aus der Importquelle überschrieben, die *bereits* im Projekt vorhanden sind.  
  
> [!NOTE]  
> Bei dieser Methode treten zwei bekannte Fehler auf, die in zukünftigen Versionen behoben sein werden:  
>   
> -   Wenn Tabellen- oder Spalteneinschränkungen außerhalb der CREATE TABLE-Anweisung in der Tabellendefinition des Projekts definiert sind, wird die Tabellendefinition beim Import überschrieben, sodass die Einschränkung inline ist. Dabei bleibt die Out-of-Line-Einschränkung jedoch bestehen, was zu doppelten Einschränkungen im Projekt führt.  
> -   Alle Masterschlüssel oder Datenbankverschlüsselungsschlüssel aus dem Quellskript, die bereits im Projekt vorhanden sind, werden beim Import dupliziert. Entfernen Sie Duplikate, um das Projekt zu erstellen.  
  
Beim Import aus Skripts können Skripts vor und nach der Bereitstellung, SQLCMD-Variablen oder RefactorLog-Dateien nicht ausgewertet werden. Diese und andere nicht unterstützte Konstrukte, die beim Import erkannt werden, werden projektweise in einer Datei **ScriptsIgnoredOnImport.sql** im Ordner **Skripts** abgelegt.  
  
Weitere Informationen finden Sie im Forum des SSDT-Teams [http://social.msdn.microsoft.com/Forums/en-US/ssdt/threads](http://social.msdn.microsoft.com/Forums/en-US/ssdt/threads).  
  
## <a name="bkmk_import_encrypted"></a>Importieren verschlüsselter Objekte  
Beim Importieren verschlüsselter Objekte in ein Datenbankprojekt kann der vollständige Text der Objektdefinition nicht immer vom Server abgerufen werden. Somit kann das Importverhalten bei der Verwendung dieser Objektklasse abweichen.  
  
Wenn der vollständige Definitionstext nicht abgerufen werden kann, werden für den Objektheader/-footer Skripts zusammen mit einem Pseudotext erstellt. Mit diesem Verhalten ist zu rechnen, wenn Sie Importieren oder Schemavergleich verwenden und es sich bei der Quelle um eine Livedatenbank oder eine aus einer Datenbank extrahierte DACPAC-Datei handelt.  
  
**Skript mit einem Pseudotext**  
  
![Skript mit einem Pseudotext](../ssdt/media/ssdt-procwithencryption.gif "Skript mit einem Pseudotext")  
  
Wenn die vollständige Objektdefinition verfügbar ist und abgerufen werden kann, wird sie bei Verwendung von Importieren und Schemavergleich vollständig in das Projekt übernommen. Dies ist der Fall, wenn das Projekt anhand eines Skripts aktualisiert bzw. eine DACPAC-Datei aus einem Datenbankprojekt oder einem anderen Projekt erstellt wird.  
  
