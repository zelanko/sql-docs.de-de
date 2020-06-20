---
title: Kompatibilitäts Grad (SSAS-tabellarisch SP1) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: f5727bd88bd04deab0e1b8364bd6cbefe9e6c142
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939871"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a>Kompatibilitätsgrad (SSAS – tabellarisch, SP1)
  Sie können den *Kompatibilitäts Grad* bei der Erstellung neuer Projekte für tabellarische Modelle, beim Aktualisieren vorhandener Projekte für tabellarische Modelle, beim Aktualisieren vorhandener tabellarischer Modell Datenbanken oder beim Importieren von Power Pivot-Arbeitsmappen angeben.  
  
## <a name="compatibility-level"></a>Kompatibilitätsgrad  
 Für gewöhnlich werden neue Versionen und Service Packs zunächst auf Entwicklungs- und Testcomputern und erst dann auf Produktionscomputern installiert. In solchen Fällen ist es wichtig, über Kenntnisse zum Festlegen des Kompatibilitätsgrads für sowohl neue Projekte für tabellarische Modelle als auch jene, die bereits in einer Produktionsumgebung bereitgestellt wurden, zu verfügen.  
  
 Eine Analysis Services-Instanz mit [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt die folgenden Kompatibilitätsgrade (Datenbankversion):  
  
-   SQL Server 2012 (1100)  
  
-   SQL Server 2012 SP1 (1103)  
  
-   SQL Server 2014 (1103)  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a>Festlegen des Kompatibilitätsgrads beim Erstellen eines neuen Projekts für tabellarische Modelle  
 Beim Erstellen eines neuen Projekts für tabellarische Modelle in SQL Server Data Tools (SSDT) können Sie im Dialogfeld **Optionen für neues tabellarisches Projekt** den Kompatibilitäts Grad angeben. Sie können bei der Erstellung eines neuen Projekts wählen, ob es in einer Analysis Services-Instanz von [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] (oder höher) oder in einer SQL Server 2012-Analysis Services-Instanz (ohne Service Pack 1) bereitgestellt werden soll.  
  
 Sie können auch einen Standardkompatibilitätsgrad angeben, indem Sie die Option **Diese Meldung nicht mehr anzeigen** aktivieren. Bei allen nachfolgenden Projekten wird der angegebene Kompatibilitätsgrad verwendet. Sie können den Standardkompatibilitätsgrad in SSDT unter "Optionen" ändern.  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a>Aktualisieren eines vorhandenen Projekts für tabellarische Modelle auf den 1103 -Kompatibilitätsgrad  
 Sie können ein tabellarisches Modellprojekt, das in SSDT erstellt wurde, vor [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] der Installation von oder höher auf die Datenbankversion 1103-kompatibel aktualisieren, indem Sie die Eigenschaft **Kompatibilitäts Grad** im Fenster **Eigenschaften** des Modells verwenden. Damit ein Projekt für tabellarische Modelle aktualisiert werden kann, muss auf dem Computer, auf dem SSDT installiert ist, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Auch auf der Analysis Services-Instanz, auf der sich die Arbeitsbereichsdatenbank befindet, muss [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Sie können nicht zu einer früheren Version herabstufen.  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a>Aktualisieren einer bereitgestellten tabellarischen Modelldatenbank auf den 1103-Kompatibilitätsgrad  
 Sie können eine vorhandene, bereitgestellte tabellarische Modelldatenbank auf die mit SQL Server Management Studio (SSMS) kompatible Datenbankversion 1103 aktualisieren, indem Sie die Eigenschaft **Kompatibilitäts Grad** in den **Daten Bank Eigenschaften**verwenden. Damit das Upgrade vorgenommen werden kann, muss auf dem Computer, auf dem die SQL Server Analysis Services-Instanz installiert ist, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Sie können eine bereitgestellte tabellarische Modelldatenbank nicht auf eine frühere Version herabstufen.  
  
### <a name="import-from-powerpivot"></a>Aus PowerPivot importieren  
 Bei der Erstellung eines neuen Projekts für tabellarische Modelle durch das Importieren aus PowerPivot können Sie angeben, ob Sie den Kompatibilitätsgrad auf den Standardkompatibilitätsgrad aktualisieren (wenn zuvor in SSDT konfiguriert) oder den Kompatibilitätsgrad beibehalten möchten, der bereits in der PowerPivot-Arbeitsmappe angegeben ist.  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a>Überprüfen des Kompatibilitätsgrads einer tabellarischen Modelldatenbank in SSMS  
 Sie können den Kompatibilitäts Grad einer tabellarischen Modelldatenbank in SSMS überprüfen, indem Sie die Eigenschaft **Kompatibilitäts Grad** (neu in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ) in den **Daten Bank Eigenschaften**anzeigen.  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a>Überprüfen des unterstützten Kompatibilitätsgrads einer Analysis Services-Instanz in SSMS  
 Sie können den unterstützten Kompatibilitäts Grad in SSMS überprüfen, indem Sie die Eigenschaft **unterstützter Kompatibilitäts Grad** auf der Seite **Informationen** (neu in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ) unter **Analysis Services Eigenschaften**anzeigen. Ein unterstützter Kompatibilitätsgrad von 1103 gibt an, dass SQL Server SP1 oder höher installiert ist. Der unterstützte Kompatibilitätsgrad kann nicht geändert werden.  
  
  
