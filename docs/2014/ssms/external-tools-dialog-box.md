---
title: Externe Tools (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15d26c23413cc3f47cba2cce5d7d7ce9efab9a66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163263"
---
# <a name="external-tools-dialog-box"></a>Externe Tools (Dialogfeld)
  Mit dem Dialogfeld **Externe Tools** können Sie dem Menü **Extras** externe Tools hinzufügen, z. B. SQLCMD oder den Editor. Durch das Hinzufügen von externen Tools können Sie auf einfache Weise andere Anwendungen starten, während Sie in der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Umgebung arbeiten. Sie können beim Starten des Tools Argumente und ein Arbeitsverzeichnis angeben. Darüber hinaus kann im **Ausgabefenster** die Ausgabe einiger Tools angezeigt werden. Das Dialogfeld **Externe Tools** wird über das Menü **Extras** aufgerufen.  
  
## <a name="options"></a>Tastatur  
 **Inhalt des Menüs**  
 Führt die Titel der Elemente auf, die aktuell dem Menü **Extras** hinzugefügt sind. Verwenden Sie die Schaltflächen **Nach oben** und **Nach unten** , um die Reihenfolge zu ändern, in der die Elemente im Menü angezeigt werden. Verwenden Sie die Schaltfläche **Löschen** , um ein Element aus dem Menü zu entfernen.  
  
 **Nach oben**  
 Verschiebt das ausgewählte Tool innerhalb der Liste der Tools im Menü **Extras** nach oben.  
  
 **Nach unten**  
 Verschiebt das ausgewählte Tool innerhalb der Liste der Tools im Menü **Extras** nach unten.  
  
 **Hinzufügen**  
 Löscht die Textfelder, sodass Sie ein neues Tool angeben können.  
  
 **Delete**  
 Entfernt das Tool oder den Befehl aus der Liste **Menüinhalt** und aus dem Menü **Extras** .  
  
 **Titel**  
 Geben Sie den Namen des Tools oder Befehls ein, der im Untermenü **Externe Tools** des Menüs **Extras** angezeigt wird. Fügen Sie vor einem Buchstaben im Namen des Tools ein kaufmännisches Und-Zeichen (&) ein, um diesen Buchstaben als Tastenkombination anzugeben. Mit „&SQLCMD“ wird z. B. SQLCMD im Menü **Extras** angezeigt.  
  
 **Befehl**  
 Gibt den Pfad zu der Datei an, die gestartet werden soll.  
  
 **Argumente**  
 Gibt die Variablen an, die an das Tool übergeben werden, wenn es im Menü aufgerufen wird. Argumente können Werte festlegen, die beim Starten an das Tool oder den Befehl übergeben werden. Ein Wert kann beispielsweise einen Dateinamen oder ein Verzeichnis angeben. Mit der Schaltfläche mit dem Pfeil können Sie aus einer Liste mit vordefinierten Argumenten auswählen. Sie können mehrere Argumente hinzufügen. Eine vollständige Liste vordefinierter Argumente und ihrer Definitionen finden Sie unter [Arguments for External Tools](menu-help/external-tools.md). Abhängig vom verwendeten Befehl oder Tool können Sie auch benutzerdefinierte Argumente eingeben, (wie z. B. Befehlszeilenoptionen).  
  
 **Ausgabefenster verwenden**  
 Öffnet das Ausgabefenster in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , in dem die Ausgabe des derzeit ausgeführten Befehls angezeigt wird. Nicht alle Tools zeigen ihre Ausgabe in einem Format an, das im Ausgabefenster dargestellt werden kann. Weitere Informationen finden Sie unter [Ausgabefenster](../relational-databases/scripting/transact-sql-debugger-output-window.md).  
  
 **Ausgabe als Unicode behandeln**  
 Interpretiert die Ausgabe als Unicode.  
  
 **Ausgangsverzeichnis**  
 Gibt das Arbeitsverzeichnis für das Tool an. Mit der Schaltfläche mit dem Pfeil können Sie Verzeichnisse auswählen. Sie können mehrere Verzeichnisse auswählen.  
  
 **Zur Argumenteingabe auffordern**  
 Zeigt das Dialogfeld **Argumente** an, in dem Sie bei jedem Start des externen Tools Werte für die Argumente eingeben oder bearbeiten können.  
  
 **Beim Beenden schließen**  
 Schließt das vom Fenster geöffnete Tool, wenn das Tool geschlossen wird.  
  
## <a name="example"></a>Beispiel  
 Durch die Eingabe der folgenden Werte im Dialogfeld **Externe Tools** wird ein Menüelement mit der Bezeichnung "DAC" erstellt. Durch Auswählen des Elements wird eine Eingabeaufforderung geöffnet und das Hilfsprogramm **sqlcmd** mithilfe der dedizierten Administratorverbindung (Dedicated Administrator Connection, DAC) ausgeführt.  
  
|Feld|value|  
|---------|-----------|  
|**Title**|DAC|  
|**Befehl**|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]Tools\Binn\SQLCMD.exe|  
|**Argumente**|-A|  
  
## <a name="see-also"></a>Siehe auch  
 [Argumente für externe Tools](menu-help/external-tools.md)   
 [Allgemeine Benutzeroberflächenelemente](general-user-interface-elements.md)  
  
  