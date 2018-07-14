---
title: Führen Sie SQL-Task-Editor (Seite Resultset) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
caps.latest.revision: 33
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 57a355411ce49b472708890c51e50eec59996dd6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269433"
---
# <a name="execute-sql-task-editor-result-set-page"></a>Editor für den Task 'SQL ausführen' (Seite Resultset)
  Mithilfe der Seite **Resultset** des Dialogfelds **Editor für den Task 'SQL ausführen'** können Sie das Ergebnis der SQL-Anweisung neuen oder vorhandenen Variablen zuordnen. Die Optionen in diesem Dialogfeld sind deaktiviert, wenn auf der Seite Allgemein für **ResultSet** der Wert **Keine**festgelegt ist.  
  
 Weitere Informationen zu diesem Task finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md) und [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Tastatur  
 **Ergebnisname**  
 Nachdem Sie durch Klicken auf **Hinzufügen**eine Resultsetzuordnung hinzugefügt haben, geben Sie einen Namen für das Ergebnis an. Je nach Resultsettyp müssen Sie bestimmte Ergebnisnamen verwenden.  
  
 Für den Resultsettyp **Einzelne Zeile**können Sie entweder den Namen einer von der Abfrage zurückgegebenen Spalte verwenden oder die Zahl, die die Position einer Spalte in der von der Abfrage zurückgegebenen Spaltenliste angibt.  
  
 Für den Resultsettyp **Vollständiges Resultset** oder **XML**müssen Sie 0 als Resultsetnamen verwenden.  
  
 **Verwandte Themen**: [Konfigurieren von Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
 **Variablenname**  
 Ordnen Sie das Resultset einer Variablen zu, indem Sie eine Variable auswählen, oder klicken Sie auf \<**Neue Variable...**>, um mithilfe des Dialogfelds **Variable hinzufügen** eine neue Variable hinzuzufügen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um eine Resultsetzuordnung hinzuzufügen.  
  
 **Entfernen**  
 Wählen Sie eine Resultsetzuordnung aus der Liste aus, und klicken Sie anschließend auf **Entfernen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task SQL ausführen &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task SQL ausführen &#40;Seite Parameterzuordnung&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 
  [Transact-SQL-Referenz &amp;#40;Datenbank-Engine&amp;#41;](/sql/t-sql/language-reference)  
  
  
