---
title: 'Lektion 2: Erstellen einer Richtlinie für einen Container und Generieren eines Shared Access Signature (SAS)-Schlüssels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 80bd9c253adfcf1d1a677953fef183d9109534ef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75231824"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Lektion 2: Erstellen einer Richtlinie für einen Container und Generieren eines Shared Access Signature (SAS)-Schlüssels
  In dieser Lektion erfahren Sie, wie Sie eine Richtlinie für den BLOB-Container erstellen und auch einen SAS-Schlüssel generieren.  
  
 Eine gespeicherte Zugriffsrichtlinie stellt eine zusätzliche Steuerungsebene für Shared Access Signatures auf Serverseite bereit. Eine Shared Access Signature ist ein URI, der eingeschränkte Zugriffsrechte für Container, BLOBs, Warteschlangen und Tabellen gewährt. Wenn Sie diese neue Erweiterung verwenden, müssen Sie eine Richtlinie für einen Container mit Lese-, Schreib- und Auflistungsrechten erstellen.  
  
 Sie können eine Richtlinie und eine Shared Access Signature erstellen, indem Sie eine der folgenden Methoden verwenden:  
  
-   Azure-Rest-API-Vorgänge: [Container erstellen](https://msdn.microsoft.com/library/azure/dd179468.aspx), [Container-ACL festlegen](https://msdn.microsoft.com/library/azure/dd179391.aspx)und [Container-ACL erhalten](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Cloudblobcontainer. getsharedaccesssignature-Methode](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) im Azure-SDK.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Ein Azure-Explorer-Tool von Drittanbietern, z. b. [Azure Storage-Explorer](https://azurestorageexplorer.codeplex.com/).  
  
 **Nächste Lektion:**  
  
 [Lektion 3: Erstellen von SQL Server-Anmeldeinformationen](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
