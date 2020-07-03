---
title: Identitätswechsel und Anmelde Informationen für Verbindungen | Microsoft-Dokumentation
description: In SQL Server CLR-Integration kann es ratsam sein, die Identität des Aufrufers bei der Windows-Authentifizierung mithilfe der SqlContext. Windows Identity-Eigenschaft anzunehmen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 0561c224a8569c2db13ab71e18d24b4a53282656
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896354"
---
# <a name="impersonation-and-credentials-for-connections"></a>Identitätswechsel und Anmeldeinformationen für Verbindungen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  In der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (Common Language Runtime)-Integration ist die Verwendung der Windows-Authentifizierung zwar komplex, jedoch sicherer als die SQL Server-Authentifizierung. Beachten Sie bei Verwendung der Windows-Authentifizierung folgende Punkte:  
  
 Standardmäßig ist für einen SQL Server-Prozess, der eine ausgehende Verbindung mit Windows herstellt, der Sicherheitskontext des Windows-Dienstkontos für SQL Server erforderlich. Es ist jedoch möglich, einer Proxyidentität eine CLR-Funktion zuzuordnen, sodass ausgehende Verbindungen einen anderen Sicherheitskontext haben als die Verbindungen des Windows-Dienstkontos.  
  
 In einigen Fällen möchten Sie möglicherweise die Identität des Aufrufers mithilfe der **SqlContext. Windows** Identity-Eigenschaft annehmen, anstatt Sie als Dienst Konto auszuführen. Die **Windows Identity-Instanz stellt** die Identität des Clients dar, der den aufrufenden Code aufgerufen hat, und ist nur verfügbar, wenn der Client die Windows-Authentifizierung verwendet hat. Nachdem Sie die **Windows** Identity-Instanz abgerufen haben, können Sie die Identität annehmen **, um** das Sicherheits Token des Threads zu ändern, und dann ADO.NET-Verbindungen für den Client öffnen.  
  
 Nachdem Sie SqlContext. Windows Identity. Imitation aufgerufen haben, können Sie nicht mehr auf lokale Daten zugreifen, und Sie können nicht auf die Systemdaten zugreifen. Um erneut auf Daten zuzugreifen, müssen Sie WindowsImpersonationContext. Undo aufrufen.  
  
 Im folgenden Beispiel wird gezeigt, wie die Identität des Aufrufers mithilfe der **SqlContext. Windows** Identity-Eigenschaft angenommen wird.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Informationen zu Verhaltensänderungen beim Identitätswechsel finden Sie unter [Breaking Changes to Datenbank-Engine Features in SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Wenn Sie die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Identitätsinstanz erhalten haben, können Sie diese Instanz standardmäßig nicht an einen anderen Computer weitergeben. Die Windows-Sicherheitsinfrastruktur schränkt diese Möglichkeit standardmäßig ein. Es gibt jedoch einen Mechanismus, der als "Delegierung" bezeichnet wird. Dieser ermöglicht die Weitergabe von Windows-Identitäten über mehrere vertrauenswürdige Computer hinweg. Weitere Informationen zur Delegierung finden Sie im TechNet-Artikel "[Kerberos-Protokoll Übergang und eingeschränkte Delegierung](https://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlContext-Objekt](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
