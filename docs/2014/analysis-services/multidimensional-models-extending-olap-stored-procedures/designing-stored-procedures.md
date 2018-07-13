---
title: Entwerfen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8311f5a4762e016fc0fae7d5594a3453aac601fa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271936"
---
# <a name="designing-stored-procedures"></a>Entwerfen von gespeicherten Prozeduren
  In gespeicherten Prozeduren ist sowohl das administrative Objektmodell "Analysis Management Objects" (AMO) als auch das clientorientierte Objektmodell "[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional)" (ADO MD) verfügbar.  
  
 Gespeicherte Prozeduren müssen sich in ihrem Gültigkeitsbereich (entweder der Server oder die Datenbank) befinden, um auf der aufzurufenden MDX-Ebene (Multidimensional Expressions) sichtbar zu sein. Nachdem eine gespeicherte Prozedur aufgerufen wurde, ist ihr Gültigkeitsbereich jedoch nicht auf Aktionen unter dem übergeordneten Element begrenzt. Eine gespeicherte Prozedur kann überall auf dem Server Änderungen vornehmen. Dabei müssen lediglich die Sicherheitseinschränkungen des Benutzerprozesses, der sie aufruft, oder die Einschränkungen der Transaktion beachtet werden, in der sie ausgeführt wird.  
  
 Serverbereichsprozeduren sind in allen Kontexten auf dem Server verfügbar. Gespeicherte Datenbankbereichsprozeduren sind nur im Datenbankkontext der Datenbank sichtbar, in der sie definiert sind.  
  
 Wie jede andere MDX-Funktion muss eine gespeicherte Prozedur aufgelöst werden, bevor eine MDX-Sitzung fortgesetzt werden kann. Während ihrer Ausführung sperren gespeicherte Prozeduren MDX-Sitzungen. Sofern nicht spezielle Gründe für das Anhalten einer MDX-Sitzung bei wartenden Benutzerinteraktionen vorliegen, wird von Benutzerinteraktionen (z. B. Dialogfeldern) abgeraten.  
  
## <a name="dependent-assemblies"></a>Abhängige Assemblys  
 Alle abhängigen Assemblys müssen in eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] geladen werden, um von der Common Language Runtime (CLR) gefunden zu werden. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] speichert die abhängigen Assemblys im gleichen Ordner wie die Hauptassembly, damit alle Verweise auf Funktionen in den Assemblys von der CLR automatisch aufgelöst werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren gespeicherter Prozeduren](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
