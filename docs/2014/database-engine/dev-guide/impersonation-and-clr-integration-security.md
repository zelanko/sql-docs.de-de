---
title: Identitätswechsel und Sicherheit der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 05b117f27d0c27ca9288f94aade079df876fafad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243200"
---
# <a name="impersonation-and-clr-integration-security"></a>Identitätswechsel und Sicherheit der CLR-Integration
  Wenn verwalteter Code auf externe Ressourcen zugreift, dann nimmt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht automatisch die Identität des aktuellen Ausführungskontexts an, in dem die Routine ausgeführt wird. Erstellen Sie Code in `EXTERNAL_ACCESS` und `UNSAFE` Assemblys können explizit die Identität des aktuellen Ausführungskontexts annehmen.  
  
> [!NOTE]  
>  Weitere Informationen zu verhaltensänderungen beim Identitätswechsel finden Sie unter [wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Der prozessinterne Datenzugriffsanbieter stellt eine Application programming Interface, `SqlContext.WindowsIdentity`, die verwendet werden kann, um das Token, das den aktuellen Sicherheitskontext zugeordnete abzurufen. In `EXTERNAL_ACCESS`-Assemblys und `UNSAFE`-Assemblys enthaltener verwalteter Code kann mit dieser Methode den Kontext abrufen und die `WindowsIdentity.Impersonate`-Methode aus .NET Framework verwenden, um die Identität dieses Kontexts anzunehmen. Die folgenden Einschränkungen gelten, wenn Benutzercode explizit einen Identitätswechsel durchführt:  
  
-   Der prozessinterne Datenzugriff ist nicht zulässig, wenn für verwalteten Code ein Identitätswechsel durchgeführt wurde. Code kann den Identitätswechsel rückgängig machen und dann den prozessinternen Datenzugriff aufrufen. Beachten Sie, dass hierzu der Rückgabewert (ein `WindowsImpersonationContext`-Objekt) der ursprünglichen `Impersonate`-Methode gespeichert und die `Undo`-Methode für dieses `WindowsImpersonationContext`-Objekt aufgerufen werden muss.  
  
     Diese Einschränkung bedeutet, dass ein prozessinterner Datenzugriff stets im Kontext des aktuellen Sicherheitskontexts erfolgt, der für die Sitzung gilt. Er kann nicht durch einen explizitem Identitätswechsel innerhalb des verwalteten Codes geändert werden.  
  
-   Bei verwaltetem Code, der asynchron ausgeführt wird (beispielsweise durch `UNSAFE`-Assemblys, die Threads erzeugen und Code asynchron ausführen) werden keine prozessinterne Datenzugriffe zugelassen. Dies gilt unabhängig davon, ob ein Identitätswechsel vorgenommen wird.  
  
 Wenn Code in einem Kontext ausgeführt wird, dessen Identität angenommen wurde und der sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterscheidet, dann kann er keine Aufrufe für prozessinterne Datenzugriffe ausführen. Bevor Aufrufe für prozessinterne Datenzugriffe ausgeführt werden, sollte der Identitätswechsel rückgängig gemacht werden. Wenn von in-Process-Datenzugriff erfolgt von verwaltetem Code, der ursprüngliche Ausführungskontext des der [!INCLUDE[tsql](../../includes/tsql-md.md)] Einstiegspunkt in den verwalteten Code wird immer für die Autorisierung verwendet.  
  
 Sowohl `EXTERNAL_ACCESS`-Assemblys als auch `UNSAFE`-Assemblys greifen über das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto auf Betriebssystemressourcen zu, sofern sie nicht freiwillig den aktuellen Sicherheitskontext wie oben beschrieben annehmen. Aufgrund der Autoren von `EXTERNAL_ACCESS` Assemblys erfordern ein höheres Maß an vertrauen, als die `SAFE` Assemblys, die angegebenen die `EXTERNAL ACCESS` -Berechtigung auf Anmeldungsebene. Nur Anmeldekonten, die vertrauenswürdig sind und unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto Code ausführen dürfen, sollten die `EXTERNAL ACCESS`-Berechtigung erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Identitätswechsel und Anmeldeinformationen für Verbindungen](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
