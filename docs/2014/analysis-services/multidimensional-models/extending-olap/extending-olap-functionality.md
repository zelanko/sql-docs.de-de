---
title: Erweitern von OLAP-Funktionalität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2d4d08795351b93615954ad64e004482745f768d
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154286"
---
# <a name="extending-olap-functionality"></a>Erweiterte von OLAP-Funktionalität
  Als Programmierer können Sie Analysis Services erweitern, indem Sie Assemblys, personalisierte Erweiterungen und gespeicherten Prozeduren schreiben, die die Funktionalität bereitstellen, die Sie in mehreren Datenbankanwendungen verwenden oder wiederverwenden möchten. Assemblys werden verwendet, um durch Hinzufügen von neuen Prozeduren und Funktionen zur MDX-Sprache oder mittels des Personalisierungs-Add-Ins die mehrdimensionale Modelle-Funktionalität zu erweitern.  
  
 Gespeicherte Prozeduren können verwendet werden, um externe Routinen aufzurufen, und vereinfachen so die Entwicklung und Implementierung von Analysis Services-Datenbanken, da gemeinsamer Code nur einmal entwickelt werden muss und an einem einzelnen Ort gespeichert werden kann. Mit gespeicherten Prozeduren kann Anwendungen Geschäftsfunktionalität hinzugefügt werden, die von der systemeigenen Funktionalität von MDX nicht bereitgestellt wird.  
  
 Personalisierungen sind benutzerdefinierte Objekte, die Sie einem Cube hinzufügen, um ein Verhalten bereitzustellen, das sich je nach Benutzer ändert. Personalisierungen sind keine permanenten Objekte im Cube, sondern Objekte, die von der Clientanwendung während der Sitzung des Benutzers dynamisch angewendet werden. Beispiele umfassen das Ändern der Währung von einem Währungswert abhängig von der Person, die auf die Daten zugreift, Bereitstellen von individualisierten KPIs oder eine gezielte Vorschlagsliste für Stammkunden, die online kaufen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erweitern von OLAP durch Personalisierungen](extending-olap-through-personalizations.md)  
  
 [Personalisierungserweiterungen für Analysis Services](analysis-services-personalization-extensions.md)  
  
 [Definieren gespeicherter Prozeduren](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
