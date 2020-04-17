---
title: Identitätswechsel und Anmeldeinformationen für Verbindungen | Microsoft Docs
description: In der SQL Server CLR-Integration können Sie die Identität des Aufrufers in der Windows-Authentifizierung mit der SqlContext.WindowsIdentity-Eigenschaft imitieren.
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
ms.openlocfilehash: 382185c036055bb9ea689f551c256a26ee83b0b4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485245"
---
# <a name="impersonation-and-credentials-for-connections"></a>Identitätswechsel und Anmeldeinformationen für Verbindungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (Common Language Runtime)-Integration ist die Verwendung der Windows-Authentifizierung zwar komplex, jedoch sicherer als die SQL Server-Authentifizierung. Beachten Sie bei Verwendung der Windows-Authentifizierung folgende Punkte:  
  
 Standardmäßig ist für einen SQL Server-Prozess, der eine ausgehende Verbindung mit Windows herstellt, der Sicherheitskontext des Windows-Dienstkontos für SQL Server erforderlich. Es ist jedoch möglich, einer Proxyidentität eine CLR-Funktion zuzuordnen, sodass ausgehende Verbindungen einen anderen Sicherheitskontext haben als die Verbindungen des Windows-Dienstkontos.  
  
 In einigen Fällen können Sie die Identität des Aufrufers mit der **SqlContext.WindowsIdentity-Eigenschaft** imitieren, anstatt als Dienstkonto ausgeführt zu werden. Die **WindowsIdentity-Instanz** stellt die Identität des Clients dar, der den aufrufenden Code aufgerufen hat, und ist nur verfügbar, wenn der Client die Windows-Authentifizierung verwendet hat. Nachdem Sie die **WindowsIdentity-Instanz** erhalten haben, können Sie **Identitätswechsel** aufrufen, um das Sicherheitstoken des Threads zu ändern, und dann ADO.NET Verbindungen im Namen des Clients öffnen.  
  
 Nachdem Sie SQLContext.WindowsIdentity.Impersonate aufzurufen, können Sie nicht mehr auf lokale Daten und nicht mehr auf Systemdaten zugreifen. Um erneut auf Daten zuzugreifen, müssen Sie WindowsImpersonationContext.Undo aufrufen.  
  
 Das folgende Beispiel zeigt, wie die Identität des Aufrufers mithilfe der **SqlContext.WindowsIdentity-Eigenschaft** angenommen wird.  
  
 Visual C#  
  
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
>  Informationen zu Verhaltensänderungen in Identitätswechsel finden Sie unter [Brechen von Änderungen an Datenbankmodulfeatures in SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Wenn Sie die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Identitätsinstanz erhalten haben, können Sie diese Instanz standardmäßig nicht an einen anderen Computer weitergeben. Die Windows-Sicherheitsinfrastruktur schränkt diese Möglichkeit standardmäßig ein. Es gibt jedoch einen Mechanismus, der als "Delegierung" bezeichnet wird. Dieser ermöglicht die Weitergabe von Windows-Identitäten über mehrere vertrauenswürdige Computer hinweg. Weitere Informationen zur Delegierung finden Sie im TechNet-Artikel "[Kerberos Protocol Transition and Constrained Delegation ".](https://go.microsoft.com/fwlink/?LinkId=50419)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlContext-Objekt](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
