---
title: Dialog Feld "Analysis-Server Eigenschaften" (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b32b0fa678df98494f91c1026adebe701d807342
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062622"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a>Eigenschaften für Analysis-Server (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Eigenschaften für Analysis-Server** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die allgemeinen, die Sprach- und Sortierungs- sowie die Sicherheitseinstellungen für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz festlegen. Zum Öffnen des Dialogfelds **Eigenschaften für Analysis-Server** klicken Sie mit der rechten Maustaste im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Objekt-Explorer** auf eine **-Instanz, und wählen Sie dann im Kontextmenü die Option **Eigenschaften** aus. Das Dialogfeld **Eigenschaften für Analysis-Server** enthält die folgenden Eigenschaften.  
  
## <a name="information-properties"></a>Informationseigenschaften  
 Verwenden Sie diese Seite, um Servermodus, Version und Kompatibilitätsgrad anzuzeigen. Jede Instanz wird entweder im tabellarischen oder mehrdimensionalen Servermodus installiert und bietet die Möglichkeit, tabellarische oder mehrdimensionale Modelle zu laden. Zur Unterstützung beider Modi müssen Sie zwei Instanzen installieren.  
  
 **Unterstützter Kompatibilitäts Grad** entspricht der `DefaultCompatibilityLevel` -Eigenschaft in AMO. Je nach dem Serverbereitstellungsmodus, der während der Installation angegeben wird, ist die Einstellung schreibgeschützt. Der Server überprüft diese Eigenschaft bei der Ausführung von Vorgängen, die je nach Servermodus oder -version variieren. Das kann z. B. die Wiederherstellung einer Sicherung einer tabellarischen Datenbank auf einer tabellarischen Serverinstanz betreffen. Verwechseln Sie die Eigenschaft nicht mit dem Datenbankkompatibilitätsmodus tabellarischer oder mehrdimensionaler Modelle, die ähnliche Namen und Werte aufweisen. Gültige Werte für diese Servereigenschaft sind:  
  
-   **1100** ist der Standard Kompatibilitäts Grad für den mehrdimensionalen und Data Mining Modus für den Bereitstellungs Modus 0.  
  
-   **1103** ist der Standard Kompatibilitäts Grad für die Bereitstellungs Modi 1 oder 2 für Installationen, die [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]den tabellarischen Modus oder unterstützen.  
  
 Der Server gibt diesen Wert zurück, wenn ein Client, von dem der Namespace unterstützt wird, DISCOVER_XML_METADATA anfordert. Weitere Einzelheiten finden Sie unter [DISCOVER_XML_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).  
  
## <a name="general-properties"></a>Allgemeine Eigenschaften  
 Mithilfe dieser Seite legen Sie die grundlegenden und erweiterten allgemeinen Eigenschaften für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz fest, z. B. Speicherorte von Ordnern und Netzwerkeinstellungen.  
  
 Auf der Seite mit Servereigenschaften werden nur die Eigenschaften angezeigt, die mit größerer Wahrscheinlichkeit von einem Administrator geändert werden, z. B. die Arbeitsspeicher- und Threadpooleigenschaften, die bei bestimmten Konfigurationen zur Serveroptimierung eingesetzt werden. Die folgende Liste enthält Links zu den wichtigsten Eigenschaftengruppen:  
  
-   [Allgemeine Eigenschaften](server-properties/general-properties.md)  
  
-   [Data Mining-Eigenschaften](server-properties/data-mining-properties.md)  
  
-   [Funktionseigenschaften](server-properties/feature-properties.md)  
  
-   [FileStore (Eigenschaften)](server-properties/filestore-properties.md)  
  
-   [Eigenschaften des Sperren-Managers](server-properties/lock-manager-properties.md)  
  
-   [Protokolleigenschaften](server-properties/log-properties.md)  
  
-   [Speichereigenschaften](server-properties/memory-properties.md)  
  
-   [Netzwerkeigenschaften](server-properties/network-properties.md)  
  
-   [OLAP-Eigenschaften](server-properties/olap-properties.md)  
  
-   [Sicherheitseigenschaften](server-properties/security-properties.md)  
  
-   [Threadpooleigenschaften](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a>Eigenschaften für Sprache/Sortierung  
 Mithilfe dieser Seite legen Sie die Standardsprache und Sortierungsoptionen für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]fest. Die folgende Liste enthält kurze Beschreibungen der einzelnen Optionen. Ausführlichere Beschreibungen finden Sie unter [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md).  
  
-   " **Binary** " wird verwendet, um Daten basierend auf den für jedes Zeichen definierten Bitmustern zu sortieren und zu vergleichen. Die binäre Sortierreihenfolge unterscheidet nach Groß-/Kleinschreibung (Kleinbuchstaben kommen immer vor Großbuchstaben) und Akzenten. Dies ist die schnellste Sortierreihenfolge.  
  
     Wenn diese Option nicht ausgewählt ist, werden von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Sortier- und Vergleichsregeln verwendet, die in Wörterbüchern für die zugeordnete Sprache oder das Alphabet definiert sind.  
  
    > [!NOTE]  
    >  Wenn diese Option ausgewählt ist, sind die Optionen **Unterscheidung nach Groß-/Kleinschreibung**, **Unterscheidung nach Akzent**, **Unterscheidung nach Kana** und **Unterscheidung nach Breite** deaktiviert.  
  
-   **Binary 2** wird verwendet, um Unicode-Daten basierend auf den für jedes Zeichen definierten Bitmustern zu sortieren und zu vergleichen. Die binäre Sortierreihenfolge unterscheidet nach Groß-/Kleinschreibung (Kleinbuchstaben kommen immer vor Großbuchstaben) und Akzenten. Dies ist die schnellste Sortierreihenfolge.  
  
-   Die Unterscheidung nach Groß **-/Kleinschreibung** wird verwendet, um Daten basierend auf den für die zugehörige Sprache oder das Alphabet bereitgestellten Wörterbuch Regeln zu sortieren und zu vergleichen und zwischen Groß-und Kleinbuchstaben zu unterscheiden  
  
     Wenn diese Option nicht ausgewählt ist, betrachtet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Groß- und Kleinschreibungsversionen von Buchstaben als gleich. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]definiert nicht, ob Kleinbuchstaben in Bezug auf Großbuchstaben unter Berücksichtigung der Groß-/Kleinschreibung unterschieden werden, wenn die groß **-** /Kleinschreibung nicht beachtet wird.  
  
-   Unterscheidung nach Akzent wird verwendet, um Daten auf der Grundlage der Wörterbuch Regeln zu sortieren und zu vergleichen, die für die zugehörige Sprache oder das Alphabet bereitgestellt werden, und um zwischen Zeichen mit **Akzent** und Zeichen ohne Akzent Beispielsweise ist 'a' nicht mit 'á' identisch.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen Buchstaben mit und ohne Akzent.  
  
-   Unterscheidung nach **Kana** wird verwendet, um Daten basierend auf den für die zugeordneten Sprache oder das Alphabet bereitgestellten Wörterbuch Regeln zu vergleichen und zwischen den beiden Typen japanischer Kana-Zeichen zu unterscheiden: Hiragana und Katakana.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen Hiragana- und Katakana-Zeichen.  
  
-   Unterscheidung nach **Breite** wird verwendet, um Daten auf der Grundlage der Wörterbuch Regeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen einem Einzel Byte Zeichen (halbe Breite) und demselben Zeichen als Doppelbyte Zeichen (volle Breite) zu unterscheiden.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen der Darstellung eines Zeichens als Einzelbyte- oder Doppelbytezeichen.  
  
## <a name="security-properties"></a>Sicherheitseigenschaften  
 Mithilfe dieser Seite geben Sie die Benutzer- und Gruppenkonten von Windows an, die bei einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz zur Rolle des Serveradministrators gehören. Die Mitgliedschaft in dieser Rolle berechtigt zur Ausführung serverweiter Aufgaben, z. B. dem Erstellen oder Verarbeiten einer Datenbank, dem Ändern von Servereigenschaften bzw. dem Hinzufügen oder Entfernen weiterer Mitglieder dieser Rolle oder dem Starten einer Ablaufverfolgung. Weitere Informationen finden Sie unter [Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bestimmen des Server Modus einer Analysis Services Instanz](instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Konfigurieren von Server Eigenschaften in Analysis Services](server-properties/server-properties-in-analysis-services.md)   
 [Von Analysis Services unterstützte Authentifizierungsmethoden](instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Rollen und Berechtigungen &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)  
  
  
