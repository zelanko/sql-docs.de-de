---
title: Erstellen von Analysis Services-Skripts in Management Studio | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28b1b0068f9ddd9bf47bc2fe93177db469c8b4f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181866"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a>Erstellen von Analysis Services-Skripts in Management Studio
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] schließt Skriptgenerierungsfunktionen, Vorlagen und Editoren ein, mit denen Sie Analysis Services-Objekte und Tasks schreiben können.  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a>Script Analysis Services-Tasks in Management Studio  
 Sie können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Skripts erstellen, indem auf eine der Skriptoptionen in einem taskbezogenen Dialogfeld geklickt wird. Alle Dialogfelder, die Sie zum Ausführen von Aufgaben verwenden (z. B. Sicherung oder Wiederherstellungsdatenbank, Objektverarbeitung oder Aggregationsentwurf), beinhalten oben eine Skriptoption. Durch die Auswahl einer dieser Optionen wird auf Grundlage der Informationen und der Einstellungen im Dialogfeld ein XMLA-Skript generiert.  
  
 Standardmäßig wird das Skript generiert und in einem XMLA-Abfrage-Editor eingefügt. Sie können die Skriptoptionsliste jedoch auch erweitern, um das Skript an die Windows-Zwischenablage oder eine Datei weiterzuleiten.  
  
#### <a name="to-script-an-analysis-services-task"></a>So erstellen Sie Skripts für einen Analysis Services-Task  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Datenbank, und klicken Sie auf **Sichern**. Daraufhin wird das Dialogfeld Datenbank sichern geöffnet. Geben Sie einen Sicherungsdateinamen an, und wählen Sie die gewünschten Optionen für diese Sicherung aus.  
  
3.  Klicken Sie auf **Skript** am oberen Rand des Dialogfelds. Die Funktion Skript ist ein Teil aller taskbasierten Dialogfelder in Management Studio. Es enthält die folgenden Optionen: **Skript für Aktion in neuem Abfragefenster** um den Abfrage-Editorfenster zu öffnen **Skript für Aktion in Datei** um das XMLA-Skript in eine Datei zu speichern oder **Skript für Aktion in Zwischenablage** der XMLA-Skript zum Speichern der Die Zwischenablage.  
  
     Beachten Sie, dass die Option **Skript für Aktion in Auftrag schreiben** , die in Management Studio als Skriptoption aufgelistet wird, für Analysis Services-Skripts nicht unterstützt wird.  
  
4.  Wenn Sie die Standardoption **Skript für Aktion in Fenster 'Neue Abfrage' schreiben**aktivieren, wird ein generiertes Skript in einem XMLA-Abfragefenster eingefügt.  
  
     Sie können jetzt das Dialogfeld Datenbank sichern und das XMLA-Skript direkt bearbeiten oder ausführen.  
  
## <a name="script-analysis-services-objects-in-management-studio"></a>Script Analysis Services-Objekte in Management Studio  
 Die Skripterstellung für Objekte mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] wird ausgeführt durch Klicken mit der rechten Maustaste auf ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und Auswählen von entweder **CREATE in**, **ALTER in**oder **DELETE in**. Jede dieser Optionen kann für ein Fenster oder eine Datei gelten, aber unabhängig davon, wofür das Skript gilt, wird es in Form eines DDL-Skripts in einem XMLA-Wrapper erstellt. Ein großer Vorteil solcher Skripts ist, dass sie auf jedem Server ausgeführt werden können, auf den Sie sie verweisen. Namen in den Skripts können geändert werden, und sie können auf iterativer Basis zur Massenerstellung, Änderung oder zur Löschung von Objekten ausgeführt werden.  
  
 Objekte, die Sie schreiben können, schließen die Elemente einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank ein, einschließlich Datenquellen, Datenquellensichten, Cubes, Dimensionen, Miningstrukturen und Rollen.  
  
 Erforderliche Komponenten schließen ein Verständnis für XML for Analysis (XMLA) ein. Glücklicherweise verfügt [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] über eine Funktion, mit der das zum Erstellen von Objekten wie Cubes benötigte XMLA-Skript automatisch erstellt wird. Diese Automatisierungsfunktion erleichtert die Verwendung von XMLA. Weitere Informationen zur Verwendung von XMLA finden Sie unter [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md). Weitere Informationen zur Verwendung von XMLA finden Sie unter [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).  
  
> [!IMPORTANT]  
>  Wenn Sie Skripts für das Role-Objekt erstellen, müssen Sie sich darüber bewusst sein, dass die Sicherheitsberechtigungen in den Objekten enthalten sind, die sie sichern, statt in der Sicherheitsrolle, der sie zugeordnet sind.  
  
#### <a name="to-script-analysis-services-objects"></a>So erstellen Sie Skripts für Analysis Services-Objekte  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her.  
  
2.  Suchen Sie das Objekt, für das Sie ein Skript zum Erstellen, Ändern oder Löschen von Objekten erstellen möchten.  
  
3.  Mit der rechten Maustaste in des Objekts, zeigen Sie auf **Skript für Cube als**, zeigen Sie auf **CREATE in**, **ALTER in**, oder **Delete in**, und klicken Sie dann auf eines der folgende Optionen: **Neues Abfrage-Editor-Fenster** zu den Abfrage-Editorfenster öffnen **Datei** um das XMLA-Skript in eine Datei zu speichern oder **Zwischenablage** um das XMLA-Skript in die Zwischenablage zu speichern.  
  
    > [!NOTE]  
    >  Normalerweise würden Sie **Datei** auswählen, wenn Sie mehrere verschiedene Versionen der Datei erstellen möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [XMLA-Abfrage-Editor &#40;Analysis Services – Mehrdimensionale Daten&#41;](http://msdn.microsoft.com/library/14623019-7839-4038-9d12-2f8953d2ec04)  
  
  
