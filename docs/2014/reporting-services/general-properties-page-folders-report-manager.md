---
title: Eigenschaftenseite "Allgemein", "Ordner (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 69330b9a1a65ed147d716d47d9a2cc68e34bab6b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056645"
---
# <a name="general-properties-page-folders-report-manager"></a>Allgemein (Eigenschaftenseite, Ordner) (Berichts-Manager)
  Verwenden Sie die Seite Allgemeine Eigenschaften für Ordner, um Eigenschaften für die von Ihnen erstellten Ordner anzuzeigen und festzulegen. Informationen zum Benutzer, der den Ordner erstellt oder geändert hat, und zum Zeitpunkt der Änderung werden oben auf der Seite Allgemeine Eigenschaften angezeigt.  
  
 Die Ordnereigenschaften schließen auch Sicherheitseinstellungen ein. Weitere Informationen zur ordnersicherheit finden Sie unter [sichere Ordner](security/secure-folders.md).  
  
 Ordner mit besonderem Zweck wie z. B. Home, Meine Berichte und Benutzerordner können weder umbenannt noch innerhalb des Namespace des Berichtsservers verschoben werden. Die Eigenschaftenseite Allgemein steht für diese Ordner nicht zur Verfügung.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a>So öffnen Sie die Seite Allgemeine Eigenschaften für einen Ordner  
  
1.  Öffnen Sie den Berichts-Manager, und öffnen Sie den Ordner, für den Sie Eigenschaften anzeigen oder konfigurieren möchten.  
  
2.  Klicken Sie unter dem Ordnerbanner auf der Symbolleiste auf **Ordnereinstellungen**.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für den Ordner an. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können nicht beim Angeben eines Namens verwendet werden: ; ? : @ & = +, $ * \< > | "oder / beim Angeben eines Namens.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Ordnerinhalts ein. Diese Beschreibung wird für Benutzer, die über die Berechtigung zum Zugreifen auf den Ordner verfügen, auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Wählen Sie diese Option aus, um den Ordner für Benutzer auszublenden, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardanzeigeformat beim Durchsuchen der Ordnerhierarchie auf dem Berichtsserver. In der Listenansicht erstrecken sich Namen und Beschreibungen über die Seite. Das alternative Format ist die Detailsansicht. Detailansichten lassen Beschreibungen aus, enthalten jedoch andere Informationen zum Element. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
 **Delete**  
 Klicken Sie auf diese Schaltfläche, um den Ordner und seinen Inhalt zu entfernen.  
  
 **Verschieben**  
 Klicken Sie auf diese Schaltfläche, um einen Bericht oder Ordner innerhalb des Namespace des Berichtsservers zu verschieben. Durch Klicken auf diese Schaltfläche wird die Seite Elemente verschieben geöffnet, auf der Sie einen anderen Ordner als Speicherort aussuchen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  