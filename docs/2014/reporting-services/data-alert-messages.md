---
title: Datenwarnmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 622fa9e74ca4195363220f00dfa7dd7875f5ba47
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109507"
---
# <a name="data-alert-messages"></a>Datenwarnmeldungen
  
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Datenwarnungen übermitteln zwei Typen von Datenwarnmeldungen per E-Mail: Meldungen mit Datenwarnungsergebnissen und Meldungen mit Fehlerbeschreibungen. Durch Meldungen mit Ergebnissen werden alle Empfänger über Änderungen der Berichtsdaten informiert, die von allgemeinem Interesse und wichtig für Geschäftsentscheidungen sind. Tritt aus einem unbestimmten Grund ein Fehler auf, und sind die Ergebnisse nicht verfügbar, wird stattdessen die Fehlermeldung gesendet.  
  
 Der Eigentümer der Datenwarnungsdefinition kann auch Informationen zur Datenwarnungsinstanz im Datenwarnungs-Manager anzeigen. Weitere Informationen finden Sie unter [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).  
  
##  <a name="DataAlertMessages"></a>Daten Warnmeldungen  
 Die folgenden Bilder zeigen eine Datenwarnmeldung mit Ergebnissen und eine Warnmeldung mit einer Fehlerbeschreibung.  
  
 **Ergebnis Meldung**  
  
 ![Datenwarnungs-E-Mail mit Ergebnissen](media/rs-alertmessageresults.gif "Datenwarnungs-E-Mail mit Ergebnissen")  
  
 **Fehlermeldung**  
  
 ![Datenwarnmeldung mit Fehlermeldung](media/rs-alertmessageerrror.gif "Datenwarnmeldung mit Fehlermeldung")  
  
 Die Meldungen beinhalten die gleichen Informationstypen.  
  
1.  **Im Namen von** enthält den Namen der Person, die die Daten Warnungs Definition erstellt hat.  
  
2.  Haben Sie in der Warnungsdefinition eine Beschreibung angegeben, wird diese unterhalb von **Im Auftrag von**angezeigt.  
  
3.  Warnungs **Ergebnisse** zeigen die Zeilen im Berichtsdaten Feed an, die den in der Warnungs Definition angegebenen Regeln im tabellarischen Format entsprechen oder eine Fehlerbeschreibung anzeigen. Die Anzahl der angezeigten Zeilen ist unbeschränkt.  
  
4.  **Gehe zu Bericht** ist ein Link zum Bericht, auf dem die Warnungs Definition basiert. Wenn der Link nicht gültig ist, da der Bericht verschoben oder gelöscht wurde, wird eine Fehlermeldung angezeigt.  
  
5.  **Regel (n)** listet die Regeln und Klauseln in der Warnungs Definition auf. Anhand dieser Informationen lassen sich die Warnungsergebnisse leichter überprüfen und verstehen. Des Weiteren lassen sich die Regeln in der Datenwarnungsdefinition identifizieren, die Sie ggf. zum Eingrenzen oder Erweitern der Ergebnisse ändern möchten.  
  
6.  **Berichts Parameter** listet die Parameter und Parameterwerte auf, die beim Ausführen des Berichts verwendet wurden. Parameter und Parameterwerte vereinfachen den Einblick in die Warnungsergebnisse.  
  
7.  Mit **Kontext Werten** werden die Namen und Werte von Berichts Elementen, die sich außerhalb der Berichtsdaten Bereiche befinden, aufgelistet. Die Elemente sind in der Regel Textfelder. Es kann sich zum Beispiel um ein Textfeld mit einem konstanten Wert wie dem Betreff oder der Beschreibung eines Berichts handeln.  
  
 Der einzige Unterschied zwischen den zwei Meldungstypen ist Element 5, **Warnungsergebnisse**. Tritt bei der Erstellung einer Datenwarnungsinstanz oder Datenwarnmeldung ein Fehler auf, zeigt **Warnungsergebnisse** eine Fehlermeldung mit der Beschreibung des Problems an. Die Fehlermeldung wird an alle Empfänger gesendet und informiert diese, dass die erwarteten Warnungsergebnisse, die die Empfänger u. U. auch für Geschäftsentscheidungen benötigen, nicht verfügbar sind.  
  
 
  
##  <a name="HowTo"></a> Verwandte Aufgaben  
 Dieser Abschnitt listet Prozeduren zum Erstellen und Bearbeiten der Datenwarnungsdefinitionen auf, die viele der in den Datenwarnmeldungen angezeigten Informationen bieten.  
  
-   [Erstellen einer Datenwarnung im Datenwarnungs-Designer](create-a-data-alert-in-data-alert-designer.md)  
  
-   [Bearbeiten einer Datenwarnung im Warnungs-Designer](edit-a-data-alert-in-alert-designer.md)  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Datenwarnungs-Designer](../../2014/reporting-services/data-alert-designer.md)   
 [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md)  
  
  
