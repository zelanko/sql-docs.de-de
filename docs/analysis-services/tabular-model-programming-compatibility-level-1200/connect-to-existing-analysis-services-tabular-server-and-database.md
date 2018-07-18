---
title: Herstellen einer Verbindung vorhandenen tabellarischen Analysis Services-Server und die Datenbank mit | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13900e4aaad52d39a2691fb40d0e419f55f660fc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033390"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Verbinden Sie mit vorhandenen tabellarischen Analysis Services-Server und Datenbank
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In SQL Server 2016 enthält Analysis Services Management Objects (AMO) mehrere Namespaces, die verwendet werden kann, um eine Server-Verbindung einzurichten. In diesem Artikel wird erläutert, wie das Herstellen eine Serververbindung mit dem Microsoft.AnalysisServices.Tabular-Namespace für Modelle und Datenbanken, die auf 1200 erstellt oder höheren Kompatibilitätsgrad. 

Zum Verbinden mit einem Analysis Services-Server muss Ihr Code eine Server-Objekt zu instanziieren und rufen Sie dann auf die Connect-Methode. Nachdem die Verbindung hergestellt ist, werden Eigenschaften des Serverobjekts die Einstellungen der aktuellen Analysis Services-Instanz angezeigt. 

Die folgenden Klassen können für Verbindungen mit der obersten Ebene verwendet werden: 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Wie Sie sehen können, wird durch zwei Namespaces bieten, Verbindungen mit Server- und Datenbankobjekte: der ursprünglichen Microsoft.AnalysisServices Namespace für AMO und den neuen Microsoft.AnalysisServices.Tabular-Namespace für TOM.

Warum zwei Namespaces für die gleichen Vorgänge? Die Antwort liegt downstream, Ebene der Datenbank- und modellsicherheitseinstellungen, in denen die Objekthierarchie wird modusspezifische und die Struktur des Modells entweder mehrdimensionale oder tabellarische Metadaten besteht. Um in der Modellstruktur aufrufen zu können, wird der Server oder Datenbank-Objekt für beide Modelltypen bereitgestellt.

> [!NOTE]  
>  Die Metadaten für die Definition des skalierungsgruppenmodells und Vorgänge ist vollständig für die beiden Modi unterschiedlich. Das Aufteilen der Datendefinitionssprache (DDL) in zwei separate Namespaces verwenden, wird für die Entwicklung durch die Präsentation der nur für einen bestimmten Modelltyp benötigten API vereinfacht. 

Obwohl die DDL-Anweisungen im Detail variiert, sind Verbindungen mit einem Server identisch für alle Modi, Versionen und Editionen. Unterstützung von einem Server und die datenbankverbindung über entweder Namespace können Sie zum Schreiben von generischen Tools oder Skripts, die mit jeder Instanz von Analysis Services herstellen oder Datenbank, ohne zu wissen, welche Art von Modell ist auf dem Server gehostet.  

Diese Flexibilität wird erläutert, die Abhängigkeiten zwischen Assemblys. Um die Aufrufe unter der Datenbank-Ebene (z. B. auf ein Modell in einem tabellarischen 1200-Datenbank oder auf einen Cube, Dimension oder Measuregruppe innerhalb einer Datenbank mehrdimensional oder Tabellarisch 1050-1103) abhängt AMO TOM. 

Im Gegensatz dazu verfügt TOM Abhängigkeit nicht in AMO. Obwohl TOM zum Durchsuchen des mehrdimensionalen Metadaten (Cubes) verwendet werden kann, kann AMO zum Durchsuchen des mehrdimensionalen und tabellarischen Metadaten verwendet werden. 

Aus diesem Grund muss der erste Schritt beim Einrichten Ihres Projekts, Hinzufügen von Verweisen auf alle AMO-Assemblys. Finden Sie unter [Verweis zu installieren und verteilen Sie die Clientbibliothek TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) Details. 

> [!NOTE]  
>  Server und Datenbankverbindungen basiert auf älteren AMO-Klassen, die von majorobject-Objekt zu erben. Obwohl Haupt-und nebenobjekte in einer Struktur des tabellarischen Modells verwendet werden, ist die MajorObject-Klasse als Basisklasse für Server- und Datenbankobjekte, die Sie zum Einrichten der Verbindung unabhängig davon, welche, die API verwenden angezeigt.  

## <a name="code-example-server-connection"></a>Codebeispiel: Server-Verbindung 

Im folgenden finden Sie ein C#-Codebeispiel, das zeigt, wie eine lokale Analysis Services-Instanz herstellen und dessen Eigenschaften in einem Konsolenfenster auflisten. 

Dieses Beispiel zeigt nur einige der Eigenschaften eines Serverobjekts, aber es gibt mehrere Eigenschaften verfügbar, einschließlich ServerMode und DefaultCompatibilityLevel.  

```
using System; 
using Microsoft.AnalysisServices.Tabular; 

namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 


            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 

 
                Console.WriteLine("Connection established successfully."); 
                Console.WriteLine(); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.WriteLine("Server name:\t\t{0}", server.Name); 
                Console.WriteLine("Server product name:\t{0}", server.ProductName); 
                Console.WriteLine("Server product level:\t{0}", server.ProductLevel); 
                Console.WriteLine("Server version:\t\t{0}", server.Version); 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```
Wenn Sie dieses Programm ausführen, zeigt die Ausgabe Eigenschaften für das Serverobjekt in einem Konsolenfenster an. 

## <a name="authentication-and-authorization"></a>Authentifizierung und Autorisierung 

Ein Server oder datenbankverbindung mit Analysis Services erfordert Administratorberechtigungen für Lese-/ Schreibvorgänge und für die Übergabe über eine Anforderung für die Verbindung mit angenommener Identität verwendet.  

Obwohl in den letzten Jahren die benutzerdefinierte Authentifizierung unter ganz bestimmten Bedingungen ermöglicht die Sicherheitsinfrastruktur von Analysis Services erweitert wurde, ist die einzige unterstützte externe Authentifizierungsmethode integrierte Sicherheit von Windows. Sicherheitsprinzipale werden als gültige Windows-Domäne Benutzer- oder Gruppenkonten angesehen.  

Unter Windows 2012 und höher, kann die Delegierung über Domänen hinweg übergeben werden. Im Analysis Services wird die Delegierung nur für DirectQuery-Modelle verwendet. Andernfalls sind die Verbindungen direkt oder dessen Identität angenommen wurde. 

## <a name="next-steps"></a>Nächste Schritte 

Nach dem Herstellen einer Verbindungs, ein nächste logischer Schritt besteht darin, entweder Auflisten von vorhandenen Datenbanken bereits auf dem Server oder möglicherweise eine neue leere Datenbank zu erstellen. Die folgenden Links enthalten Codebeispiele, in denen beide grundlegenden Aufgaben veranschaulicht: 

- [Erstellen und Bereitstellen einer leeren Datenbank](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Listen vorhandener Datenbanken auf](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
