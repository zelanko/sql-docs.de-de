---
description: Dienstanbieter und -komponenten
title: Dienstanbieter und Komponenten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f0c89d8a7f83bebfa77fb02a282fc21cb6f2dd0
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724941"
---
# <a name="service-providers-and-components"></a>Dienstanbieter und -komponenten
Dienstanbieter sind Komponenten, die die Funktionalität von Datenanbietern durch die Implementierung erweiterter Schnittstellen erweitern, die vom Datenspeicher nicht nativ unterstützt werden.  
  
 Der universelle Datenzugriff bietet eine *Komponentenarchitektur* , mit der einzelne, spezialisierte Komponenten diskrete Sätze von Datenbankfunktionen oder "Dienste" auf der Grundlage weniger fähiger Speicher implementieren können. Daher stellen Dienst Komponenten eine gängige Implementierung dar, die jede Anwendung für den Zugriff auf einen beliebigen Datenspeicher verwenden kann, anstatt zu erzwingen, dass die einzelnen Datenspeicher eine eigene Implementierung erweiterter Funktionen bereitstellen oder generische Anwendungen erzwingen, dass Datenbankfunktionen intern implementiert werden. Die Tatsache, dass einige Funktionen System intern vom Datenspeicher implementiert werden, und einige über generische Komponenten sind für die Anwendung transparent.  
  
 Beispielsweise ist eine Cursor-Engine, z. b. [der Cursor Dienst für OLE DB](/previous-versions/windows/desktop/ms714397(v=vs.85)), eine Dienst Komponente, die Daten aus einem sequenziellen, vorwärts gerichteten Datenspeicher nutzen kann, um scrollbare Daten zu erzeugen. Andere Dienstanbieter, die häufig von ADO verwendet werden, beinhalten den Microsoft OLE DB Dauerhaftigkeits [Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (zum Speichern von Daten in einer Datei), den Microsoft-Daten Strukturierungs [Dienst für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (für hierarchische **Recordsets**) und den [Microsoft OLE DB Remoting-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)  
  
 Weitere Informationen zu Dienst-und Datenanbietern finden Sie unter [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).