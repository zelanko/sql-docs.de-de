---
title: Dienstanbieter und Komponenten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a78db07f5ba445c54108558b2ff222bd217c2bbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924248"
---
# <a name="service-providers-and-components"></a>Dienstanbieter und -komponenten
Dienstanbieter sind Komponenten, die die Funktionalität von Datenanbietern durch die Implementierung erweiterter Schnittstellen erweitern, die vom Datenspeicher nicht nativ unterstützt werden.  
  
 Der universelle Datenzugriff bietet eine *Komponentenarchitektur* , mit der einzelne, spezialisierte Komponenten diskrete Sätze von Datenbankfunktionen oder "Dienste" auf der Grundlage weniger fähiger Speicher implementieren können. Anstatt zu erzwingen, dass jeder Datenspeicher seine eigene Implementierung erweiterter Funktionen bereitstellt oder generische Anwendungen zwingt, die Datenbankfunktionalität intern zu implementieren, stellen Dienst Komponenten eine gängige Implementierung dar, die jede Anwendung Verwenden Sie, wenn Sie auf einen beliebigen Datenspeicher zugreifen. Die Tatsache, dass einige Funktionen System intern vom Datenspeicher implementiert werden, und einige über generische Komponenten sind für die Anwendung transparent.  
  
 Beispielsweise ist eine Cursor-Engine, z. b. [der Cursor Dienst für OLE DB](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), eine Dienst Komponente, die Daten aus einem sequenziellen, vorwärts gerichteten Datenspeicher nutzen kann, um scrollbare Daten zu erzeugen. Andere Dienstanbieter, die häufig von ADO verwendet werden, beinhalten den Microsoft OLE DB Dauerhaftigkeits [Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (zum Speichern von Daten in einer Datei), den Microsoft-Daten Strukturierungs [Dienst für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (für hierarchische **Recordsets**) und den [Microsoft OLE DB Remoting-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)  
  
 Weitere Informationen zu Dienst-und Datenanbietern finden Sie unter [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).
