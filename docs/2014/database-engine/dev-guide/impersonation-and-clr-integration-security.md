---
title: Identitätswechsel und Sicherheit der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2c32691a065c2bfc43868d6b4105fbf1395a63ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62781128"
---
# <a name="impersonation-and-clr-integration-security"></a>Identitätswechsel und Sicherheit der CLR-Integration
  Wenn verwalteter Code auf externe Ressourcen zugreift, dann nimmt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht automatisch die Identität des aktuellen Ausführungskontexts an, in dem die Routine ausgeführt wird. Der in einer `EXTERNAL_ACCESS`-Assembly und einer `UNSAFE`-Assembly enthaltene Code kann explizit die Identität des aktuellen Ausführungskontexts annehmen.  
  
> [!NOTE]  
>  Weitere Informationen zu verhaltensänderungen beim Identitätswechsel finden Sie unter [wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Der prozessinterne Datenzugriffsanbieter stellt die Anwendungsprogrammierschnittstelle `SqlContext.WindowsIdentity` zur Verfügung, mit der das Token abgerufen werden kann, das dem aktuellen Sicherheitskontext zugeordnet ist. In `EXTERNAL_ACCESS`-Assemblys und `UNSAFE`-Assemblys enthaltener verwalteter Code kann mit dieser Methode den Kontext abrufen und die `WindowsIdentity.Impersonate`-Methode aus .NET Framework verwenden, um die Identität dieses Kontexts anzunehmen. Die folgenden Einschränkungen gelten, wenn Benutzercode explizit einen Identitätswechsel durchführt:  
  
-   Der prozessinterne Datenzugriff ist nicht zulässig, wenn für verwalteten Code ein Identitätswechsel durchgeführt wurde. Code kann den Identitätswechsel rückgängig machen und dann den prozessinternen Datenzugriff aufrufen. Beachten Sie, dass hierzu der Rückgabewert (ein `WindowsImpersonationContext`-Objekt) der ursprünglichen `Impersonate`-Methode gespeichert und die `Undo`-Methode für dieses `WindowsImpersonationContext`-Objekt aufgerufen werden muss.  
  
     Diese Einschränkung bedeutet, dass ein prozessinterner Datenzugriff stets im Kontext des aktuellen Sicherheitskontexts erfolgt, der für die Sitzung gilt. Er kann nicht durch einen explizitem Identitätswechsel innerhalb des verwalteten Codes geändert werden.  
  
-   Bei verwaltetem Code, der asynchron ausgeführt wird (beispielsweise durch `UNSAFE`-Assemblys, die Threads erzeugen und Code asynchron ausführen) werden keine prozessinterne Datenzugriffe zugelassen. Dies gilt unabhängig davon, ob ein Identitätswechsel vorgenommen wird.  
  
 Wenn Code in einem Kontext ausgeführt wird, dessen Identität angenommen wurde und der sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterscheidet, dann kann er keine Aufrufe für prozessinterne Datenzugriffe ausführen. Bevor Aufrufe für prozessinterne Datenzugriffe ausgeführt werden, sollte der Identitätswechsel rückgängig gemacht werden. Wenn ein prozessinterner Datenzugriff aus verwaltetem Code erfolgt, dann wird immer der ursprüngliche Ausführungskontext des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Einstiegspunkts in den verwalteten Code zur Autorisierung verwendet.  
  
 Sowohl `EXTERNAL_ACCESS`-Assemblys als auch `UNSAFE`-Assemblys greifen über das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto auf Betriebssystemressourcen zu, sofern sie nicht freiwillig den aktuellen Sicherheitskontext wie oben beschrieben annehmen. Daher benötigen die Autoren von `EXTERNAL_ACCESS`-Assemblys eine höhere Vertrauensebene als die Autoren von `SAFE`-Assembly; die Vertrauensebene wird durch die `EXTERNAL ACCESS`-Berechtigung auf Anmeldungsebene festgelegt. Nur Anmeldekonten, die vertrauenswürdig sind und unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto Code ausführen dürfen, sollten die `EXTERNAL ACCESS`-Berechtigung erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Identitätswechsel und Anmeldeinformationen für Verbindungen](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
