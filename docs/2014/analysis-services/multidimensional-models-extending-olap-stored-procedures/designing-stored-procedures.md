---
title: Entwerfen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545362"
---
# <a name="designing-stored-procedures"></a>Entwerfen von gespeicherten Prozeduren
  In gespeicherten Prozeduren ist sowohl das administrative Objektmodell "Analysis Management Objects" (AMO) als auch das clientorientierte Objektmodell "[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional)" (ADO MD) verfügbar.  
  
 Gespeicherte Prozeduren müssen sich in ihrem Gültigkeitsbereich (entweder der Server oder die Datenbank) befinden, um auf der aufzurufenden MDX-Ebene (Multidimensional Expressions) sichtbar zu sein. Nachdem eine gespeicherte Prozedur aufgerufen wurde, ist ihr Gültigkeitsbereich jedoch nicht auf Aktionen unter dem übergeordneten Element begrenzt. Eine gespeicherte Prozedur kann überall auf dem Server Änderungen vornehmen. Dabei müssen lediglich die Sicherheitseinschränkungen des Benutzerprozesses, der sie aufruft, oder die Einschränkungen der Transaktion beachtet werden, in der sie ausgeführt wird.  
  
 Serverbereichsprozeduren sind in allen Kontexten auf dem Server verfügbar. Gespeicherte Datenbankbereichsprozeduren sind nur im Datenbankkontext der Datenbank sichtbar, in der sie definiert sind.  
  
 Wie jede andere MDX-Funktion muss eine gespeicherte Prozedur aufgelöst werden, bevor eine MDX-Sitzung fortgesetzt werden kann. Während ihrer Ausführung sperren gespeicherte Prozeduren MDX-Sitzungen. Sofern nicht spezielle Gründe für das Anhalten einer MDX-Sitzung bei wartenden Benutzerinteraktionen vorliegen, wird von Benutzerinteraktionen (z. B. Dialogfeldern) abgeraten.  
  
## <a name="dependent-assemblies"></a>Abhängige Assemblys  
 Alle abhängigen Assemblys müssen in eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] geladen werden, um von der Common Language Runtime (CLR) gefunden zu werden. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] speichert die abhängigen Assemblys im gleichen Ordner wie die Hauptassembly, damit alle Verweise auf Funktionen in den Assemblys von der CLR automatisch aufgelöst werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellen](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren von gespeicherten Prozeduren](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
