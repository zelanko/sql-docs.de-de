---
title: Sicherheit bei der CLR-Integration | Microsoft-Dokumentation
description: SQL Server Integration in die .NET Framework CLR-Sicherheit verwaltet den Zugriff zwischen Objekten. Die für Objekte ausgeführten Sicherheitsüberprüfungen sind von den beteiligten aufrufen abhängig.
ms.custom: ''
ms.date: 07/22/2020
ms.prod: sql
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
ms.openlocfilehash: 7774d83d959bccea3a1de1d7d0a06660d52c191b
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641903"
---
# <a name="clr-integration-security"></a>Sicherheit der CLR-Integration

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Das Sicherheitsmodell der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Integration in die [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-CLR (Common Language Runtime) dient zur Verwaltung und zum Schutz des Zugriffs auf verschiedene Typen von CLR-Objekten und anderen Objekten, die in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt werden. Diese Objekte werden möglicherweise durch eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung oder ein anderes CLR-Objekt, das im Server ausgeführt wird, aufgerufen. Die Aufrufe zwischen Objekten werden als Links bezeichnet. Die Typen von Sicherheitsüberprüfungen, die für diese Objekte ausgeführt werden, hängen von den betroffenen Linktypen ab.  
  
 Das Sicherheitsmodell der CLR Integration dient folgenden Zielen:  
  
-   Standardmäßig sollte durch die Ausführung von verwaltetem Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Integrität und Stabilität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht beeinträchtigt werden. Die Durchführung von Vorgängen, die die Stabilität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potenziell beeinträchtigen, sollte durch entsprechende Berechtigungen auf höherer Ebene geschützt werden.  
  
-   Verwalteter Benutzercode sollte keinen unbefugten Zugriff auf Benutzerdaten oder anderen in der Datenbank enthaltenen Benutzercode erhalten. Benutzerdefinierter Code sollte in dem Sicherheitskontext der Benutzersitzung, in der er aufgerufen wurde, und mit den richtigen Berechtigungen für diesen Sicherheitskontext ausgeführt werden.  
  
-   Der Benutzercode sollte durch geeignete Maßnahmen daran gehindert werden, auf Ressourcen außerhalb des Servers zuzugreifen, sodass er ausschließlich für den Zugriff auf lokale Daten und Berechnungen genutzt wird.  
  
-   Benutzerdefinierter Code sollte nicht in der Lage sein, nur deshalb unbefugten Zugriff auf Systemressourcen zu erlangen, weil er im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozess ausgeführt wird.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kombiniert jetzt das benutzerbasierte Sicherheitsmodell von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem auf dem Codezugriff basierenden Sicherheitsmodell der CLR. Einige Vorteile dieses kombinierten Sicherheitsansatzes werden in diesem Abschnitt erläutert.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [CLR-Integration und Codezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
 Erläutert das Codezugriffssicherheitsmodell für verwalteten Code.  
  
 [Hostschutzattribute und Programmierung der CLR-Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Stellt Informationen zu den Hostschutzattributwerten bereit, die in SAFE-Assemblys und EXTERNAL_ACCESS-Assemblys nicht zulässig sind.  
  
 [Links in Sicherheit der CLR-Integration]()  
 Beschreibt, wie Teile von Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einander aufrufen können.  
  
 [Identitätswechsel und Sicherheit der CLR-Integration](../data-access/impersonation-and-credentials-for-connections.md)  
 Erläutert, wie verwalteter Code mithilfe des Identitätswechsels auf externe Ressourcen zugreift.  
  
 Erläutert Probleme, die auftreten, wenn eine verwaltete Methode eine Methode in einer Klasse aufruft, die in einer anderen Assembly enthalten ist.  
  
 [Anwendungsdomänen und Sicherheit der CLR-Integration](/previous-versions/sql/2014/database-engine/dev-guide/allowing-partially-trusted-callers?view=sql-server-2014&preserve-view=true)  
 Beschreibt, wie Assemblys in Anwendungsdomänen geladen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR-Integrationsassemblys](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
  
