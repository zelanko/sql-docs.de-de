---
title: Verwalten von Dateien mit Codierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a30c0ffe6aabe46866d6b2e09b945bc1682898ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095100"
---
# <a name="manage-files-with-encoding"></a>Verwalten von Dateien mit Codierung
  Um die Anzeige von Code in einer bestimmten Sprache und auf einer bestimmten Plattform zu vereinfachen, können Sie einer Datei eine bestimmte Zeichencodierung zuordnen.  
  
## <a name="opening-files"></a>Öffnen von Dateien  
 Sie können zum Bearbeiten der Datei einen Editor Ihrer Wahl verwenden.  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a>So öffnen Sie eine Datei mit einem bestimmten Editor  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Wählen Sie im Dialogfeld **Datei öffnen** den Dateinamen aus.  
  
3.  Klicken Sie auf den Pfeil neben der Schaltfläche **Öffnen** , und klicken Sie dann im angezeigten Menü auf**Öffnen mit** .  
  
4.  Wählen Sie in der Liste **Wählen Sie das zu öffnende Programm aus** einen Editor aus, und klicken Sie dann auf **Öffnen**. Wählen Sie zum Öffnen einer Datei mit einer bestimmten Codierung einen Editor mit Codierungsunterstützung aus, z. B. den SQL-Abfrage-Editor mit Codierung oder den XML-Editor mit Codierung.  
  
## <a name="saving-files"></a>Speichern von Dateien  
 Sie können Code auch mit Unicode-Codierung oder einer anderen Codepage speichern, um verschiedene Sprachen zu unterstützen, z. B. Westeuropäisch oder Osteuropäisch. Sie können einer Datei eine bestimmte Zeichencodierung zuordnen, um die Anzeige von Code in dieser Sprache zu vereinfachen, sowie einen Zeilenendentyp zur Unterstützung eines bestimmten Betriebssystems. Darüber hinaus können einige Zeichen in Dateinamen nur gespeichert werden, wenn sie mit Unicode-Codierung gespeichert werden.  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a>So speichern Sie eine Datei mit einer anderen Codierung oder einem anderen Zeilenendentyp  
  
1.  Auf der **Datei** Menü klicken Sie auf **speichern \<Filename > als**.  
  
2.  Erweitern Sie im Dialogfeld **Datei speichern unter** die Schaltfläche **Speichern** , und klicken Sie dann auf **Mit Codierung speichern**.  
  
3.  Wählen Sie im Dialogfeld **Erweiterte Speicheroptionen** in der Liste **Codierung** die gewünschte Codierung aus.  
  
4.  Wählen Sie in der Liste **Zeilenenden**den gewünschten Zeilenendentyp aus.  
  
    > [!NOTE]  
    >  Wenn Sie die Datei mit Unicode-Codierung speichern, muss die Datei in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe als Binärdatei eingecheckt werden, da Visual SourceSafe keine Unterstützung für das Zusammenführen, Vergleichen und Anzeigen von Unterschieden zwischen Dateien bietet, die mit Unicode-Codierung gespeichert werden.  
  
 Wenn Sie mit Visual SourceSafe Dateien mit ANSI-, UTF8- oder Unicode-Codierung speichern, beachten Sie die folgenden Einschränkungen:  
  
-   Bei ANSI-Dateien sind nur Zeichen zulässig, die in der aktuellen Codepage unterstützt werden, wodurch die internationale Verwendung eingeschränkt ist.  
  
-   Bei Unicode-Dateien können die Funktionen zum freigegebenen Auschecken, Überprüfen von Unterschieden oder Zusammenführen nicht verwendet werden, da sie als Binärdateien behandelt werden. Sie können dieses Format in internationalen Dateien verwenden.  
  
-   UTF8-Dateien funktionieren nicht sicher mit Visual SourceSafe, da Änderungen, die für Editoren von UTF8-Dateien Probleme verursachen, beim Einchecken, Auschecken, Überprüfen von Unterschieden und Zusammenführen vorgenommen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Dateien, die Projektmappen und Projekte verwalten](files-that-manage-solutions-and-projects.md)   
 [Zuordnen von Dateierweiterungen zu einem Code-Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
