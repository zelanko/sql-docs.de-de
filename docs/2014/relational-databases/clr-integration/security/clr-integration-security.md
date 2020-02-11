---
title: Sicherheit bei der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 12ca3fcb00122313c1d1e4aae8b64733be9140c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62918990"
---
# <a name="clr-integration-security"></a>Sicherheit der CLR-Integration
  Das Sicherheitsmodell des [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) verwaltet und schützt den Zugriff zwischen verschiedenen Typen von CLR-und nicht-CLR-Objekten [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] , die innerhalb einer Anweisung ausgeführt werden, oder einem anderen CLR-Objekt, das auf dem Server ausgeführt wird. Die Aufrufe zwischen Objekten werden als Links bezeichnet. Die Typen von Sicherheitsüberprüfungen, die für diese Objekte ausgeführt werden, hängen von den betroffenen Linktypen ab.  
  
 Das Sicherheitsmodell der CLR Integration dient folgenden Zielen:  
  
-   Standardmäßig wird der verwaltete Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt. Die Durchführung von Vorgängen, die die Stabilität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potenziell beeinträchtigen, sollte durch entsprechende Berechtigungen auf höherer Ebene geschützt werden.  
  
-   Verwalteter Benutzercode sollte keinen unbefugten Zugriff auf Benutzerdaten oder anderen in der Datenbank enthaltenen Benutzercode erhalten. Benutzerdefinierter Code sollte in dem Sicherheitskontext der Benutzersitzung, in der er aufgerufen wurde, und mit den richtigen Berechtigungen für diesen Sicherheitskontext ausgeführt werden.  
  
-   Der Benutzercode sollte durch geeignete Maßnahmen daran gehindert werden, auf Ressourcen außerhalb des Servers zuzugreifen, sodass er ausschließlich für den Zugriff auf lokale Daten und Berechnungen genutzt wird.  
  
-   Benutzerdefinierter Code sollte nicht in der Lage sein, nur deshalb unbefugten Zugriff auf Systemressourcen zu erlangen, weil er im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozess ausgeführt wird.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]mit dem Code Zugriffs basierten Sicherheitsmodell der CLR. Einige Vorteile dieses kombinierten Sicherheitsansatzes werden in diesem Abschnitt erläutert.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [CLR-Integration und Codezugriffssicherheit](clr-integration-code-access-security.md)  
 Erläutert das Codezugriffssicherheitsmodell für verwalteten Code.  
  
 [Hostschutzattribute und Programmierung der CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Stellt Informationen zu den Hostschutzattributwerten bereit, die in SAFE-Assemblys und EXTERNAL_ACCESS-Assemblys nicht zulässig sind.  
  
 [Links in Sicherheit der CLR-Integration](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 Beschreibt, wie Teile von Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einander aufrufen können.  
  
 [Identitätswechsel und Sicherheit der CLR-Integration](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 Erläutert, wie verwalteter Code mithilfe des Identitätswechsels auf externe Ressourcen zugreift.  
  
 [Zulassen von teilweise vertrauenswürdigen Aufrufern](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 Erläutert Probleme, die auftreten, wenn eine verwaltete Methode eine Methode in einer Klasse aufruft, die in einer anderen Assembly enthalten ist.  
  
 [Anwendungsdomänen und Sicherheit der CLR-Integration](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 Beschreibt, wie Assemblys in Anwendungsdomänen geladen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR-Integrationsassemblys](../assemblies/managing-clr-integration-assemblies.md)  
  
  
