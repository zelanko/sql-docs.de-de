---
title: Kompatibilitätsgrad (SSAS – tabellarisch, SP1) | Microsoft-Dokumentation
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
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4c04690906d9b5f3fd38ddf444d6c3f99e917a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299000"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a>Kompatibilitätsgrad (SSAS – tabellarisch, SP1)
  Sie können angeben, *Kompatibilitätsgrad* bei der Erstellung neuer Projekte für tabellarische Modelle, beim Aktualisieren bestehender Projekte für tabellarische Modelle, beim Aktualisieren bestehender tabellarischer modelldatenbanken bereitgestellter oder beim Importieren von PowerPivot-Arbeitsmappen.  
  
## <a name="compatibility-level"></a>Kompatibilitätsgrad  
 Für gewöhnlich werden neue Versionen und Service Packs zunächst auf Entwicklungs- und Testcomputern und erst dann auf Produktionscomputern installiert. In solchen Fällen ist es wichtig, über Kenntnisse zum Festlegen des Kompatibilitätsgrads für sowohl neue Projekte für tabellarische Modelle als auch jene, die bereits in einer Produktionsumgebung bereitgestellt wurden, zu verfügen.  
  
 Eine Analysis Services-Instanz mit [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt die folgenden Kompatibilitätsgrade (Datenbankversion):  
  
-   SQL Server 2012 (1100)  
  
-   SQL Server 2012 SP1 (1103)  
  
-   SQL Server 2014 (1103)  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a>Festlegen des Kompatibilitätsgrads beim Erstellen eines neuen Projekts für tabellarische Modelle  
 Beim Erstellen eines neuen tabellenmodellprojekts in SQL Server Data Tools (SSDT) für die **Optionen für neues tabellarisches Projekt** Dialogfeld können Sie den Kompatibilitätsgrad angeben. Sie können bei der Erstellung eines neuen Projekts wählen, ob es in einer Analysis Services-Instanz von [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] (oder höher) oder in einer SQL Server 2012-Analysis Services-Instanz (ohne Service Pack 1) bereitgestellt werden soll.  
  
 Sie können auch einen Standardkompatibilitätsgrad angeben, indem Sie die Option **Diese Meldung nicht mehr anzeigen** aktivieren. Bei allen nachfolgenden Projekten wird der angegebene Kompatibilitätsgrad verwendet. Sie können den Standardkompatibilitätsgrad in SSDT unter "Optionen" ändern.  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a>Aktualisieren eines vorhandenen Projekts für tabellarische Modelle auf den 1103 -Kompatibilitätsgrad  
 Sie können ein Projekt für tabellarische Modelle in SSDT erstelltes, vor der Installation aktualisieren [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher, auf die Datenbankversion 1103 kompatibel sein, mit der **Kompatibilitätsgrad** Eigenschaft im Modell **Eigenschaften**Fenster. Damit ein Projekt für tabellarische Modelle aktualisiert werden kann, muss auf dem Computer, auf dem SSDT installiert ist, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Auch auf der Analysis Services-Instanz, auf der sich die Arbeitsbereichsdatenbank befindet, muss [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Sie können nicht zu einer früheren Version herabstufen.  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a>Aktualisieren einer bereitgestellten tabellarischen Modelldatenbank auf den 1103-Kompatibilitätsgrad  
 Sie können eine vorhandenen bereitgestellten tabellarischen Modell-Datenbank auf kompatible Datenbankversion 1103 in SQL Server Management Studio (SSMS) aktualisieren, indem Sie mit der **Kompatibilitätsgrad** -Eigenschaft in **Datenbankeigenschaften**. Damit das Upgrade vorgenommen werden kann, muss auf dem Computer, auf dem die SQL Server Analysis Services-Instanz installiert ist, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder höher installiert sein. Sie können eine bereitgestellte tabellarische Modelldatenbank nicht auf eine frühere Version herabstufen.  
  
### <a name="import-from-powerpivot"></a>Aus PowerPivot importieren  
 Bei der Erstellung eines neuen Projekts für tabellarische Modelle durch das Importieren aus PowerPivot können Sie angeben, ob Sie den Kompatibilitätsgrad auf den Standardkompatibilitätsgrad aktualisieren (wenn zuvor in SSDT konfiguriert) oder den Kompatibilitätsgrad beibehalten möchten, der bereits in der PowerPivot-Arbeitsmappe angegeben ist.  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a>Überprüfen des Kompatibilitätsgrads einer tabellarischen Modelldatenbank in SSMS  
 Sie können den Kompatibilitätsgrad einer tabellarischen Modelldatenbank in SSMS überprüfen, anhand der **Kompatibilitätsgrad** Eigenschaft (neu in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Datenbankeigenschaften**.  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a>Überprüfen des unterstützten Kompatibilitätsgrads einer Analysis Services-Instanz in SSMS  
 Sehen Sie anhand den unterstützte Kompatibilitätsgrad in SSMS die **unterstützter Kompatibilitätsgrad** Eigenschaft für die **Informationen** Seite (neu in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Eigenschaften von Services**. Ein unterstützter Kompatibilitätsgrad von 1103 gibt an, dass SQL Server SP1 oder höher installiert ist. Der unterstützte Kompatibilitätsgrad kann nicht geändert werden.  
  
  
