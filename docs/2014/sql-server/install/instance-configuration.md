---
title: Instanzkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66329d4c25a23a6b3dbc3570723bab8aecfa3d4a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68190968"
---
# <a name="instance-configuration"></a>Instanzkonfiguration
  Verwenden Sie die Seite **Instanzkonfiguration** des Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um anzugeben, ob eine Standardinstanz oder eine benannte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt werden soll. Wenn noch keine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Server installiert wurde, wird eine Standardinstanz erstellt, es sei denn Sie geben eine benannte Instanz an.  
  
 Jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz besteht aus einem Satz von Diensten mit bestimmten Einstellungen für Sortierungen und andere Optionen. Verzeichnisstruktur, Registrierungsstruktur und Dienstnamen spiegeln den Instanznamen und die von Ihnen bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angegebene Instanz-ID wider.  
  
 Bei der Instanz kann es sich um eine Standardinstanz oder um eine benannte Instanz handeln. Der Name der Standardinstanz lautet MSSQLSERVER. Es ist kein Client erforderlich, um den Instanznamen zur Herstellung einer Verbindung anzugeben. Eine benannte Instanz wird vom Benutzer während des Setups festgelegt. Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als benannte Instanz installieren, ohne zuvor die Standardinstanz zu installieren. Es kann jeweils nur eine Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unabhängig von der Version, als Standardinstanz fungieren.  
  
 **Warnung!** Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep können Sie den Instanznamen angeben, wenn Sie auf der Seite **Instanzkonfiguration** eine vorbereitete Instanz abschließen. Sie können die vorbereitete Instanz, die Sie abschließen, als Standardinstanz konfigurieren, wenn sich auf dem Computer keine vorhandene Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
## <a name="multiple-instances"></a>Mehrere Instanzen  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem einzelnen Server oder Prozessor, es kann jedoch nur eine einzige Instanz als Standardinstanz fungieren. Alle anderen müssen benannte Instanzen sein. Auf einem Computer können mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gleichzeitig ausgeführt werden, und jede Instanz wird unabhängig von den anderen Instanzen ausgeführt.  
  
 Weitere Informationen finden Sie unter [Spezifikationen der maximalen Kapazität für SQL Server](../maximum-capacity-specifications-for-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 Nur Failoverclusterinstanzen: Geben Sie den Netzwerknamen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusters an. Anhand dieses Namens wird die Failoverclusterinstanz im Netzwerk identifiziert.  
  
 Standardinstanz oder benannte Instanz: Bei der Entscheidung der Frage, ob eine Standardinstanz oder eine benannte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden soll, müssen folgende Informationen beachtet werden:  
  
-   Wenn Sie eine einzelne Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Datenbankserver installieren möchten, sollte dies eine Standardinstanz sein.  
  
-   Verwenden Sie eine benannte Instanz , wenn Sie mehrere Instanzen auf dem gleichen Computer verwenden möchten. Ein Server kann nur als Host für eine einzelne Standardinstanz dienen.  
  
-   Jede Anwendung, die [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installiert, sollte die Installation als benannte Instanz vornehmen. Dadurch werden die Konflikte für den Fall minimiert, dass mehrere Anwendungen auf demselben Computer installiert werden.  
  
 **Standardinstanz**  
 Wählen Sie diese Option aus, um eine Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu installieren. Ein Computer kann nur als Host für eine Standardinstanz dienen, alle anderen Instanzen müssen benannt sein. Wenn eine Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist, ist es jedoch möglich, demselben Computer eine Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] hinzufügen.  
  
 **Benannte Instanz**  
 Wählen Sie diese Option aus, um eine neue benannte Instanz zu erstellen. Beachten Sie beim Benennen einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Folgendes:  
  
-   Bei Instanznamen wird die Groß-/Kleinschreibung nicht berücksichtigt.  
  
-   Instanznamen dürfen nicht mit einem Unterstrich (_) beginnen oder enden.  
  
-   Instanznamen dürfen keine Begriffe wie "Standard" oder andere reservierte Schlüsselwörter enthalten. Wenn in einem Instanznamen ein reserviertes Schlüsselwort verwendet wird, tritt ein Setupfehler auf. Weitere Informationen finden Sie unter [reservierte Schlüsselwörter &#40;Transact-SQL-&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql).  
  
-   Wenn Sie MSSQLServer als Instanznamen angeben, wird eine Standardinstanz erstellt.  
  
-   Eine Installation von [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] wird immer als benannte Instanz von 'PowerPivot' installiert. Sie können keinen anderen Instanznamen für diese Funktionsrolle angeben.  
  
-   Instanznamen können maximal 16 Zeichen enthalten.  
  
-   Das erste Zeichen eines Instanznamens muss ein Buchstabe sein. Akzeptable Buchstaben sind diejenigen, die durch Unicode Standard 2.0 definiert werden. Dazu gehören die lateinischen Zeichen a-z, A-Z sowie Buchstaben aus anderen Sprachen.  
  
-   Bei den anderen Zeichen kann es sich um Buchstaben des Unicode-Standards 2.0, Dezimalzeichen aus dem lateinischen Grundalphabet oder anderen nationalen Schriften, das Dollarzeichen ($) oder einen Unterstrich (_) handeln.  
  
-   Eingebettete Leerzeichen und sonstige Sonderzeichen sind in Instanznamen nicht zugelassen. Umgekehrte Schrägstriche (\\), Kommas (,), Doppelpunkte (:), Strichpunkte (;), einfache Anführungszeichen ('), kaufmännische Und-Zeichen (&), Bindestriche (-) und das At-Zeichen (@) sind ebenfalls nicht zulässig.  
  
-   **In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanznamen können nur Zeichen verwendet werden, die in der aktuellen Windows-Codepage gültig sind. Wenn ein nicht unterstütztes Unicode-Zeichen verwendet wird, tritt ein Setup Fehler auf.**  
  
 **Erkannte Instanzen und Funktionen**  
 Zeigt eine Liste der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen und Komponenten an, die auf dem Computer installiert sind, auf dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausgeführt wird.  
  
 **Instanz-ID** : Standardmäßig wird der Instanzname als Instanz-ID verwendet. Das Ziel ist dabei, Installationsverzeichnisse und Registrierungsschlüssel für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu identifizieren. Dies ist der Fall für Standardinstanzen und benannte Instanzen. Bei einer Standardinstanz lauten Instanzname und Instanz-ID MSSQLSERVER. Wenn Sie eine nicht standardmäßige Instanz-ID verwenden möchten, geben Sie Sie im Feld **Instanz-ID** an.  
  
> [!IMPORTANT]  
>  Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep handelt es sich bei der auf dieser Seite angezeigten Instanz-ID um die Instanz-ID, die Sie während des Schritts Image vorbereiten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep-Prozesses angegeben haben. Sie sind nicht in der Lage, während des Schritts Image abschließen eine andere Instanz-ID anzugeben.  
  
> [!NOTE]  
>  Instanz-IDs, die mit einem Unterstrich (_) beginnen oder das Nummernzeichen (#) oder Dollarzeichen ($) enthalten, werden nicht unterstützt.  
  
 Weitere Informationen zu Verzeichnissen, Dateispeicher Orten und Namen der Instanz-ID finden Sie unter [Dateispeicher Orte für Standard Instanzen und benannte Instanzen von SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).  
  
 Alle Komponenten einer gegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden als Einheit verwaltet. Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Service Packs und Updates werden für jede Komponente einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]übernommen.  
  
 Alle Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die denselben Instanznamen verwenden, müssen die folgenden Kriterien erfüllen:  
  
-   **Gleiche Version**  
  
-   **Gleiche Edition**  
  
-   **Gleiche Spracheinstellungen**  
  
-   **Gleicher gruppierter Status**  
  
    > [!NOTE]  
    >  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist nicht clusterabhängig.  
  
-   **Gleiches Betriebssystem**  
  
  
