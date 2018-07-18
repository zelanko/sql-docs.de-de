---
title: Dialogfeld "Analysis Services-Eigenschaften" (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e3dfe081a2400c795b8c0bd08a5667eaa996268
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260014"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a>Eigenschaften für Analysis-Server (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Eigenschaften für Analysis-Server** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die allgemeinen, die Sprach- und Sortierungs- sowie die Sicherheitseinstellungen für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz festlegen. Zum Öffnen des Dialogfelds **Eigenschaften für Analysis-Server** klicken Sie mit der rechten Maustaste im **Objekt-Explorer** auf eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz, und wählen Sie dann im Kontextmenü die Option **Eigenschaften** aus. Das Dialogfeld **Eigenschaften für Analysis-Server** enthält die folgenden Eigenschaften.  
  
## <a name="information-properties"></a>Informationseigenschaften  
 Verwenden Sie diese Seite, um Servermodus, Version und Kompatibilitätsgrad anzuzeigen. Jede Instanz wird entweder im tabellarischen oder mehrdimensionalen Servermodus installiert und bietet die Möglichkeit, tabellarische oder mehrdimensionale Modelle zu laden. Zur Unterstützung beider Modi müssen Sie zwei Instanzen installieren.  
  
 **Unterstützter Kompatibilitätsgrad** entspricht der `DefaultCompatibilityLevel` -Eigenschaft in AMO. Je nach dem Serverbereitstellungsmodus, der während der Installation angegeben wird, ist die Einstellung schreibgeschützt. Der Server überprüft diese Eigenschaft bei der Ausführung von Vorgängen, die je nach Servermodus oder -version variieren. Das kann z. B. die Wiederherstellung einer Sicherung einer tabellarischen Datenbank auf einer tabellarischen Serverinstanz betreffen. Verwechseln Sie die Eigenschaft nicht mit dem Datenbankkompatibilitätsmodus tabellarischer oder mehrdimensionaler Modelle, die ähnliche Namen und Werte aufweisen. Gültige Werte für diese Servereigenschaft sind:  
  
-   **1100** ist der standardmäßige Kompatibilitätsgrad, wenn für den mehrdimensionalen und Data Mining-Modus der Bereitstellungsmodus 0 konfiguriert wurde.  
  
-   **1103** ist der standardmäßige Kompatibilitätsgrad, wenn für Installationen, die den tabellarischen Modus oder [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]unterstützen, der Bereitstellungsmodus 1 oder 2 konfiguriert wurde.  
  
 Der Server gibt diesen Wert zurück, wenn ein Client, von dem der Namespace unterstützt wird, DISCOVER_XML_METADATA anfordert. Weitere Einzelheiten finden Sie unter [DISCOVER_XML_METADATA-Rowset](schema-rowsets/xml/discover-xml-metadata-rowset.md).  
  
## <a name="general-properties"></a>Allgemeine Eigenschaften  
 Mithilfe dieser Seite legen Sie die grundlegenden und erweiterten allgemeinen Eigenschaften für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz fest, z. B. Speicherorte von Ordnern und Netzwerkeinstellungen.  
  
 Auf der Seite mit Servereigenschaften werden nur die Eigenschaften angezeigt, die mit größerer Wahrscheinlichkeit von einem Administrator geändert werden, z. B. die Arbeitsspeicher- und Threadpooleigenschaften, die bei bestimmten Konfigurationen zur Serveroptimierung eingesetzt werden. Die folgende Liste enthält Links zu den wichtigsten Eigenschaftengruppen:  
  
-   [Allgemeine Eigenschaften](server-properties/general-properties.md)  
  
-   [Data Mining-Eigenschaften](server-properties/data-mining-properties.md)  
  
-   [Funktionseigenschaften](server-properties/feature-properties.md)  
  
-   [Dateispeichereigenschaften](server-properties/filestore-properties.md)  
  
-   [Eigenschaften des Sperren-Managers](server-properties/lock-manager-properties.md)  
  
-   [Protokolleigenschaften](server-properties/log-properties.md)  
  
-   [Speichereigenschaften](server-properties/memory-properties.md)  
  
-   [Netzwerkeigenschaften](server-properties/network-properties.md)  
  
-   [OLAP-Eigenschaften](server-properties/olap-properties.md)  
  
-   [Sicherheitseigenschaften](server-properties/security-properties.md)  
  
-   [Threadpooleigenschaften](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a>Eigenschaften für Sprache/Sortierung  
 Mithilfe dieser Seite legen Sie die Standardsprache und Sortierungsoptionen für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]fest. Die folgende Liste enthält kurze Beschreibungen der einzelnen Optionen. Ausführlichere Beschreibungen finden Sie unter [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md).  
  
-   **Binär** wird verwendet, um Daten basierend auf den für jedes Zeichen definierten Bitmustern zu sortieren und zu vergleichen. Die binäre Sortierreihenfolge unterscheidet nach Groß-/Kleinschreibung (Kleinbuchstaben kommen immer vor Großbuchstaben) und Akzenten. Dies ist die schnellste Sortierreihenfolge.  
  
     Wenn diese Option nicht ausgewählt ist, werden von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Sortier- und Vergleichsregeln verwendet, die in Wörterbüchern für die zugeordnete Sprache oder das Alphabet definiert sind.  
  
    > [!NOTE]  
    >  Wenn diese Option ausgewählt ist, sind die Optionen **Unterscheidung nach Groß-/Kleinschreibung**, **Unterscheidung nach Akzent**, **Unterscheidung nach Kana**und **Unterscheidung nach Breite** deaktiviert.  
  
-   **Binär 2** wird verwendet, um Unicode-Daten basierend auf den für jedes Zeichen definierten Bitmustern zu sortieren und zu vergleichen. Die binäre Sortierreihenfolge unterscheidet nach Groß-/Kleinschreibung (Kleinbuchstaben kommen immer vor Großbuchstaben) und Akzenten. Dies ist die schnellste Sortierreihenfolge.  
  
-   **Unterscheidung nach Groß-/Kleinschreibung** wird verwendet, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen Groß- und Kleinschreibung zu unterscheiden.  
  
     Wenn diese Option nicht ausgewählt ist, betrachtet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Groß- und Kleinschreibungsversionen von Buchstaben als gleich. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definiert nicht, ob Kleinbuchstaben niedriger oder einsortiert höher als Großbuchstaben Wenn **Groß-/Kleinschreibung** nicht ausgewählt ist.  
  
-   **Unterscheidung nach Akzent** wird verwendet, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen Buchstaben mit und ohne Akzent zu unterscheiden. Beispielsweise ist 'a' nicht mit 'á' identisch.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen Buchstaben mit und ohne Akzent.  
  
-   **Unterscheidung nach Kana** wird verwendet, um Daten basierend auf den für die zugehörige Sprache oder das Alphabet bereitgestellten Wörterbuchregeln zu sortieren und zu vergleichen und zwischen den beiden japanischen Kanazeichentypen zu unterscheiden: Hiragana und Katakana.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen Hiragana- und Katakana-Zeichen.  
  
-   **Unterscheidung nach Breite** wird verwendet, um Daten auf der Grundlage der Wörterbuchregeln zu sortieren und zu vergleichen, die für die zugeordnete Sprache oder das Alphabet bereitgestellt werden, und um zwischen einem Einzelbytezeichen (halbe Breite) und demselben Zeichen als Doppelbytezeichen (normale Breite) zu unterscheiden.  
  
     Wenn diese Option nicht ausgewählt ist, unterscheidet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht zwischen der Darstellung eines Zeichens als Einzelbyte- oder Doppelbytezeichen.  
  
## <a name="security-properties"></a>Sicherheitseigenschaften  
 Mithilfe dieser Seite geben Sie die Benutzer- und Gruppenkonten von Windows an, die bei einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz zur Rolle des Serveradministrators gehören. Die Mitgliedschaft in dieser Rolle berechtigt zur Ausführung serverweiter Aufgaben, z. B. dem Erstellen oder Verarbeiten einer Datenbank, dem Ändern von Servereigenschaften bzw. dem Hinzufügen oder Entfernen weiterer Mitglieder dieser Rolle oder dem Starten einer Ablaufverfolgung. Finden Sie unter [Erteilen von Serveradministratorberechtigungen &#40;Analysis Services&#41; ](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) Details.  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen des Servermodus einer Analysis Services-Instanz](instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Konfigurieren von Servereigenschaften in Analysis Services](server-properties/server-properties-in-analysis-services.md)   
 [Von Analysis Services Unterstützte Authentifizierungsmethoden](instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Rollen und Berechtigungen &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)  
  
  
